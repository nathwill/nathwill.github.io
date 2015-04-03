---
layout: post
title: Auto-generating make targets for packer templates
---

Simple example of auto-generating Make targets for a suite
of packer templates, using Chef and Docker.

## Makefile

{% highlight make %}
projs := $(basename $(wildcard *.json))
cmds := validate inspect build fix

# Enable packer debug logging
PACKER_LOG := 1
PACKER_LOG_PATH := /tmp/packer-debug
export PACKER_LOG PACKER_LOG_PATH

# call out rules that don't generate output 
.PHONY: clean deps \
	$(cmds) $(foreach proj,$(projs), $(addsuffix -$(proj),$(cmds))) \
	all $(projs)

# dep management tasks
clean:
	@rm -rf cookbooks

deps: cookbooks

cookbooks:
	@berks vendor $@

# auto-define global and per-proj rules for packer commands
define packer_cmd_rules
$1: $(addprefix $1-,$(projs))
$(addprefix $1-,$(projs)):
	@packer $1 $$(addsuffix .json,$$(subst $1-,,$$@))
endef

$(foreach cmd,$(cmds), $(eval $(call packer_cmd_rules,$(cmd))))

# auto generate global and per-proj fast-builds
all: $(projs)

$(projs):
	@packer build \
		-var "base_image=${@}" \
		$(addsuffix .json, $@)
{% endhighlight %}

## Packer Template

{% highlight raw %}
{
  "description": "build docker image",
  "min_packer_version": "0.7.5",
  "variables": {
    "base_image": "centos"
  },
  "builders": [
    {
      "type": "docker",
      "image": "{{user `base_image`}}",
      "run_command": ["-d", "-i", "-t", "{{.Image}}", "/bin/bash", "--noprofile", "--norc"],
      "commit": true
    }
  ],
  "provisioners": [
    {
      "type": "shell",
      "script": "scripts/setup.sh"
    },
    {
      "type": "chef-solo",
      "prevent_sudo": true,
      "cookbook_paths": ["site-cookbooks", "cookbooks"],
      "run_list": ["my-org::default"]
    },
    {
      "type": "file",
      "source": "tests",
      "destination": "/tmp"
    },
    {
      "type": "shell",
      "script": "scripts/validate.sh"
    },
    {
      "type": "shell",
      "script": "scripts/cleanup.sh"
    }
  ],
  "post-processors": [
    {
      "type": "docker-tag",
      "repository": "my-org/image",
      "tag": "{{timestamp}}"
    },
    {
      "type": "docker-tag",
      "repository": "my-org/image",
      "tag": "latest"
    }
  ]
}
{% endhighlight %}

## Result

{% highlight bash %}
[nathwill@wyrd ~]$ ls *.json
derp.json  shoop.json  woops.json
[nathwill@wyrd ~]$ make <tab> <tab>
all             build-shoop     cookbooks       fix             fix-woops       inspect-shoop   validate        validate-woops
build           build-woops     deps            fix-derp        inspect         inspect-woops   validate-derp   woops
build-derp      clean           derp            fix-shoop       inspect-derp    shoop           validate-shoop
{% endhighlight %}

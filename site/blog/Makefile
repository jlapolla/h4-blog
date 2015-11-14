# Check for posts/ build module
ifeq ($(wildcard $(d)posts/Makefile),) # If posts/ build module is not installed
  # Download posts/ build module
  include exec.mk
  $(call exec,git clone https://github.com/jlapolla/h4-blog-content.git $(d)posts,Failed to download "$(d)posts/" module)
endif # End check for posts/ build module

##
# Populate the article page template with contents
#
# USAGE
# $(call populate_template,main.html,head.html,config.yml)
#
# @param main.html  Path to article body partial HTML file
# @param head.html  Path to article head content partial HTML file
# @param config.yml Path to article configuration YAML file
$(eval populate_template = $(d)populate-template $(d)template.html $$(1) $$(2) $$(3))

include require.mk
posts_exports := $(call require,$(addsuffix Makefile,$(d)posts/))

define $(d)template
.PHONY: $(d)clean
$(d)clean: $(addsuffix clean,$(d)posts/)
endef

$(eval $($(d)template))
$(eval $(d)template :=)

exports := $(posts_exports)

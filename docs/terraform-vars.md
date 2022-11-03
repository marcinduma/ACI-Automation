# Terraform Variables

As you can see in the previous lab, manually specifying each resource and its values is very time consuming. In this lab you will learn how to use variables and functions to simplify the work

## 1. Variable file

Variable declarations can appear anywhere in your configuration files. However, it is recommended putting them into a separate file called variables.tf to make it easier for users to understand how the configuration is meant to be customized.

To parameterize an argument with an input variable, you will first define the variable in `variables.tf`, then replace the hardcoded value with a reference to that variable in your configuration.

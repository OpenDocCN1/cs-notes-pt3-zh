# ## 2.2 regular expression

# ### 3. Comment

# #### Several forms:

/* this is a C comment */ ba(~(ab))*ab (wrong)

"/**" ([^*/] | [^*] "/" | "*" [^/]) * "*"/"

not include /*/. 。 。 。 。

not include /****/

"/" ""/" " * ([^*/] | [^*] "/" | " " [^/]) * "" " * " * "*/ "

{ this is a pascal comment } {{(~}) *}}

; this is a schema comment

-- this is an Ada comment --(~newline)*
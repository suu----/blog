# ElCapitanにしたらTeXlipseでコンパイルできなくなった  
ElCapitanにするまえに、MacTeXを最新版2015に更新して、アップデート  
パスを変更してTeXlipseで以前の原稿をコンパイルしようとするとコンパイルできなかった。以下の様なエラーが出てた。  
  
```
Errors occurred during the build.
Errors running builder 'Latex Builder' on project 'HOGE'.
Building the project: 
Cannot run program "/usr/local/texlive/2015basic/bin/x86_64-darwin/luajittex" (in directory "/Users/hogehoge/workspace/piyopiyo"): error=2, No such file or directory
```  
  
PATHを見たりSIPを切ってみたりしたものの解決せず。  
  
# 解決策  
EclipseのバージョンがKeplerだったので最新版のMarsに変更したら直った  
  
# その後  
コンパイルされるようになったがlualatexがエラー出してPDFができず。  
ltluatex.texがおかしいみたい。  
以下log  
  
**hoge.log**  
```logos:hoge.log
lualatex> This is LuaTeX, Version beta-0.80.0 (TeX Live 2015) (rev 5238) 
lualatex>  restricted \write18 enabled.
lualatex> (./document.tex
lualatex> LaTeX2e <2015/01/01>
lualatex> Babel <3.9l> and hyphenation patterns for 21 languages loaded.
lualatex> (/usr/local/texlive/2015basic/texmf-dist/tex/luatex/luatexja/ltjsarticle.cls
lualatex> Document Class: ltjsarticle 2015/05/26 
lualatex> (/usr/local/texlive/2015basic/texmf-dist/tex/luatex/luatexja/luatexja.sty
lualatex> (/usr/local/texlive/2015basic/texmf-dist/tex/luatex/luatexja/luatexja-core.sty
lualatex> (/usr/local/texlive/2015basic/texmf-dist/tex/luatex/luaotfload/luaotfload.sty
lualatex> (/usr/local/texlive/2015basic/texmf-dist/tex/luatex/luatexbase/luatexbase.sty
lualatex> (/usr/local/texlive/2015basic/texmf-dist/tex/luatex/ctablestack/ctablestack.sty
lualatex> (/usr/local/texlive/2015basic/texmf-dist/tex/latex/base/ltluatex.tex
lualatex> ! Missing number, treated as zero.
lualatex> <to be read again> 
lualatex> \relax 
lualatex> l.140 \newcatcodetable\catcodetable@initex
lualatex>                                         
lualatex> ! No room for a new 8.
lualatex> \e@ch@ck ...lse \errmessage {No room for a new #4}
lualatex>                                                   \fi \fi 
lualatex> l.140 \newcatcodetable\catcodetable@initex
lualatex>                                         
lualatex> 
lualatex> ! LaTeX Error: Missing \begin{document}.
lualatex> 
lualatex> See the LaTeX manual or LaTeX Companion for explanation.
lualatex> Type  H <return>  for immediate help.
lualatex>  ...                                              
lualatex>                                                   
lualatex> l.140 \newcatcodetable\catcodetable@initex
lualatex>                                         
lualatex> ! Invalid \catcode table.
lualatex> <recently read> \allocationnumber 
lualatex>                   
lualatex> l.140 \newcatcodetable\catcodetable@initex
lualatex>                                         
lualatex> ! Missing number, treated as zero.
lualatex> <to be read again> 
lualatex> \relax 
lualatex> l.140 \newcatcodetable\catcodetable@initex
lualatex>                                         
lualatex> ! Missing number, treated as zero.
lualatex> <to be read again> 
lualatex> \relax 
lualatex> l.141 \newcatcodetable\catcodetable@string
lualatex>                                         
lualatex> ! No room for a new 8.
lualatex> \e@ch@ck ...lse \errmessage {No room for a new #4}
lualatex>                                                   \fi \fi 
lualatex> l.141 \newcatcodetable\catcodetable@string
lualatex>                                         
lualatex> ! Missing number, treated as zero.
lualatex> <to be read again> 
lualatex> \relax 
lualatex> l.141 \newcatcodetable\catcodetable@string
lualatex>                                         
lualatex> ! Invalid \catcode table.
lualatex> \newcatcodetable ...atcodetable \allocationnumber 
lualatex>                                                   
lualatex> l.141 \newcatcodetable\catcodetable@string
lualatex>                                         
lualatex> )
lualatex> Runaway definition?
lualatex> #1#2#3{\ifnum #1>#2 \expandafter \@gobble \else \expandafter \@firsto\ETC.
lualatex> ! File ended while scanning definition of \setrangecatcode.
lualatex> <inserted text> 
lualatex> }
lualatex> l.10   \input{ltluatex}
lualatex>                      %
lualatex> ! Missing { inserted.
lualatex> <inserted text> }
lualatex>  
lualatex> l.10   \input{ltluatex}
lualatex>                      %
lualatex> )
lualatex> Runaway definition?
lualatex> setcatcodetable#1#2{\begingroup #2\savecatcodetable #1\endgroup } \def \ETC.
lualatex> ! File ended while scanning definition of \@.
lualatex> <inserted text> 
lualatex> }
lualatex> l.18   \fi
lualatex>         
lualatex> ! Missing { inserted.
lualatex> <inserted text> }
lualatex>  
lualatex> l.18   \fi
lualatex>         
lualatex> )
lualatex> Runaway definition?
lualatex> #1{\directlua {require("#1")}\@gobbleoptarg } \ifdefined \@ifnextchar \ETC.
lualatex> ! File ended while scanning definition of \RequireLuaModule.
lualatex> <inserted text> 
lualatex> }
lualatex> l.45 \fi
lualatex>       
lualatex> ! Missing { inserted.
lualatex> <inserted text> }
lualatex>  
lualatex> l.45 \fi
lualatex>       
lualatex> ! Use of \RequireLuaModule doesn't match its definition.
lualatex> l.46 \RequireLuaModule{
lualatex>                      luaotfload-main}
lualatex> 
lualatex> Overfull \hbox (20.0pt too wide) in paragraph at lines 140--47
lualatex> [][]000000
lualatex> )
lualatex> 
lualatex> ! LaTeX Error: File `{.sty' not found.
lualatex> 
lualatex> Type X to quit or <RETURN> to proceed,
lualatex> or enter new name. (Default extension: sty)
lualatex> 
```  

# list-of-acronyms
Just a list of acronyms that I use in LaTeX

## History

Just acretes over time... previous version on a [gist](https://gist.github.com/larsvilhuber/169753e43f3ef938c0db1410ffd34a44).

## Usage

### Simple

Download, and drop into your LaTeX directory for your paper.
```
\usepackage{acronym}
%\usepackage[printonlyused]{acronym}
```

and somewhere (usually in an appendix)
```
\input{acronyms.tex}
```

In the text,
```
% Usage in the later text:
%  \ac{acronym}         Expand and identify the acronym the first time; use
%                       only the acronym thereafter
%  \acf{acronym}        Use the full name of the acronym.
%  \acs{acronym}        Use the acronym, even before the first corresponding
%                       \ac command
%  \acl{acronym}        Expand the acronym without using the acronym itself.
```

## Alternative

If you don't want the acronyms to be listed, use the alternative "`\acrodef{}{}`
".

```
\usepackage{acronym}
\input{acrodefs.tex} 
```

where you created `acrodefs.tex` as 
```
grep -v "{acronym}" acronyms.tex | sed 's/acro{/acrodef{/' > acrodefs.tex
``` 

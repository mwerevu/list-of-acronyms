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

## Alternative Alternative

If you are interested in trying out the [acro package](https://ctan.org/pkg/acro) but don't want to re-type the acronym list in the new syntax, you can use the following to convert to the simplest representation of the acronym definition:

```
grep acrodef acronyms.tex | sed  's/acrodef{\(.*\)}{\(.*\)}/DeclareAcronym{\U\1\E}{short = \U\1\E, long = \2}/' > acroacronyms.tex
```

Note that this puts the acronym IDs in uppercase, but there are additional options in the package to ignore case on the IDs if you like.

Then you can use this file as:

```
\usepackage{acro}
\input{acroacronyms.tex}
```

And if you want to include a list of acronyms, you can use:

```
\printacronyms
```

which comes with lots of options.

IMPORTANT: The acro package doesn't like duplicate entries, so you will have to clean the duplicates out of this list before it will compile correctly.

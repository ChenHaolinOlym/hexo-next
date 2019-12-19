---
title: Tips for Writing LaTex Code
tags: [tex, usage, tips, note, latex]
mathjax: true
categories:
  - note
  - tex
date: 2019-09-03 15:03:51
---

## Commands

### Logical Operators

Name | Symbol | Code
:-: | :-: | :-:
negation | $\neg$ | `\lnot` or `\neg`
overline | $\overline{overline}$ | `\overline{overline}`
and | $\land$ | `\wedge` or `\land`
or | $\vee$ | `\lor` or `\vee`
exclusive-or | $\oplus$ | `\oplus`
equivalence | $\equiv$ | `\equiv`
tautology | $\top{}$ | `\top`
contradiction | $\bot$ | `\bot`
universal quantification | $\forall$ | `\forall`
existential quantification | $\exists$ | `\exists`
Because | $\because$ | `\because`
Therefore | $\therefore$ | `\therefore`

### Greek Letters

Symbol | Code
:-: | :-:
A / $\alpha$ | `A` / `\alpha`
B / $\beta$ | `B` / `\beta`
$\Gamma$ / $\gamma$ | `\Gamma` / `\gamma`
$\Delta$ / $\delta$ | `\Delta` / `\delta`
E / $\epsilon$ / $\varepsilon$ | `E` / `\epsilon` / `\varepsilon`
Z / $\zeta$ | `Z` / `\zeta`
H / $\eta$ | `H` / `\eta`
$\Theta$ / $\theta$ / $\vartheta$ | `\Theta` / `\theta` / `\vartheta`
I / $\iota$ | `I` / `\iota`
K / $\kappa$ / $\varkappa$ | `K` / `\kappa` / `\varkappa`
$\Lambda$ / $\lambda$ | `\Lambda` / `\lambda`
M / $\mu$ | `M` / `\mu`
N / $\nu$ | `N` / `\nu`
$\Xi$ / $\xi$ | `\Xi` / `\xi`
O / $\omicron$ | `O` / `\omicron` 
$\Pi$ / $\pi$ / $\varpi$ | `\Pi` / `\pi` / `\varpi`
$P$ / $\rho$ / $\varrho$ | `P` / `\rho` / `\varrho` 
$\Sigma$ / $\sigma$ / $\varsigma$ | `\Sigma` / `\sigma` / `\varsigma`
$T$ / $\tau$ | `\T` / `\tau` 
$\Upsilon$ / $\upsilon$ | `\Upsilon` / `\upsilon`
$\Phi$ / $\phi$ / $\varphi$ | `\Phi` / `\phi` / `\varphi`
$X$ / $\chi$ | `X` / `\chi` 
$\Psi$ / $\psi$ | `\Psi` / `\psi`
$\Omega$ / $\omega$ | `\Omega` / `\omega`

### Relation Operators

Name | Symbol | Code
:-: | :-: | :-:
Not less than | $\nless$ | `\nless`
Not greater than | $\ngtr$ | `\ngtr`
Less than or equal to | $\leq$ / $\leqslant$ | `\leq` / `\leqslant`
Greater than or equal to | $\geq$ / $\geqslant$ | `\geq` / `\geqslant`
Neither less than nor equal to | $\nleq$ / $\nleqslant$ | `\nleq` / `\nleqslant`
Neither greater than nor equal to | $\ngeq$ / $\ngeqslant$ | `\ngeq` / `\ngeqslant`
Is member of | $\in$ | `\in`
Has member | $\ni$ | `\ni`
Is not member of | $\not\in$ | `\not\in`
Hasn't member | $\not\ni$ | `\not\ni`
Is a proper subset of | $\subset$ | `\subset`
Is a proper superset of | $\supset$ | `\supset`
Is not a proper subset of | $\not\subset$ | `\subset`
Is not a proper superset of | $\not\supset$ | `\supset`
Is a subset of | $\subseteq$ | `\subseteq`
Is a superset of | $\supseteq$ | `\supseteq`
Is not a subset of | $\not\subseteq$ | `\subseteq`
Is not a superset of | $\not\supseteq$ | `\supseteq`
Approximately | $\approx$ | `\approx`
Not equal to | $\neq$ | `\neg` / `\ne`

### Others

Name | Symbol | Code
:-: | :-: | :-:
overset | $\overset{over}{N}$ | `\overset{over}{N}`
underset | $\underset{under}{N}$ | `\underset{under}{N}`
binom | $\binom{a}{b}$ | `\binom{a}{b}` 
ceil | $\lceil x \rceil$ | `\lceil x \rceil` 
floor | $\lfloor x \rfloor$ | `\lfloor x \rfloor` 

## Escapes

### In hexo

Command | Represents
:-: | :-:
`\_` | `_`
`\\\\` | `\\`(It is the break line symbol of)
`&` | `&`(hexo will take care of the "&" escape for you)

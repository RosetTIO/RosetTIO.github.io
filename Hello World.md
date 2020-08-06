# Hello, World!

<!--
TODO:
Update COW

MOST DEFINITELY NOT OPTIMAL:
Surface
HBCHT
YABALL

Almost certainly not optimal:
SNUSP (Modular)
Bitwise Fuckery
Boolfuck
\/
AlphaBeta
Archway2
Malbolge
CSL
Sad-Flak
Shtriped
Starry
Unicat
Symbolic Python
Glypho (can use CSL as starting point - has rot and rrot though so will not be optimal): [...s].reverse().map(c=>({'p':'abbb','1':'aabc','~':'aabb','+':'aabcabba','-':'aabcabcaabba','D':'abab','*':'abbc','&':'abba'})[c]).join('')
Glypho (shorthand): [...s].reverse().map(c=>({'p':'o','1':'1','~':'\\','+':'1+','-':'1-+','D':'d','*':'*','&':'+'})[c]).join('')
To normal: [...s].replace(/./g,m=>({n:'aaaa',i:'aaab','>':'aaba','\\':'aabb',1:'aabc','<':'abaa',d:'abab','[':'abac','+':'abba',o:'abbb','*':'abbc','-':'abca',']':'abcb','!':'abcc','e':'abcd'})[m])
Gaot++:
import re
code = """\
36 $ + $ $ p
29 + $ p
7 + $ p
$ p
$ 3 + p
32 $ 12 + p
p
rev 15 + $ p rev
$ 3 + $ p
3 + p
p
13 + p
33 p"""
lookup = ["+", "-", "skip", "end", "<", "iff", "ift", "P", "p", "R", "r", "$", "~", "rev", "%"]
def codify(word):
	word = word.group()
	if word in lookup:
		return "blee%st" % ("e" * lookup.index(word))
	return "ba" + "a" * int(word)
result = re.sub(r"\w+|[^ \r\n\t\v]", codify, code)
print len(result)
print(result)

Probably not optimal:
;#+
Beam
brainbool
Brainbash
COW

May be optimal:
3var
Brainfuck (&derivatives)
Brain-Flak (&derivatives)
Commentator
99
Cubix
Flipbit
Forked
Minimal-2D
Simplefunge
Stones
Unreadable
Beatnik
Subskin
Grass:
cat > grassy.py <<'EOF'
stack=['i','w','+1','o']
program=''
isfn=False
def fn(name, args, body):
	global stack, program, isfn
	local_stack = stack[:] + args
	if program!='': program += 'v'
	program += 'w' * len(args)
	for s in body:
		argname, fnname, varname = s.split(' ')
		program += (
			'W' * (1 + local_stack[::-1].index(fnname)) +
			'w' * (1 + local_stack[::-1].index(varname))
		)
		local_stack += [argname]
	stack += [name]
	isfn = True
def var(resname, fnname, varname):
	global stack, program, isfn
	if isfn: program += 'v'
	program += 'W' * (1 + stack[::-1].index(fnname))
	program += 'w' * (1 + stack[::-1].index(varname))
	stack += [resname]
	isfn = False
def vars(s):
	lines = s.split('\n')
	for line in lines:
		var(*line.split(' '))
# hello world
fn('+3', ['x'], ['y +1 x', 'z +1 y', 'a +1 z'])
fn('twice', ['f','x'], ['y f x', 'z f y']) # wut??
vars('''\
4times twice twice
+4 4times +1
+8 twice +4
+32 4times +8
+64 twice +32''')
fn('_c23', ['f'], ['c183 +64 w', 'c247 +64 c183', 'c23 +32 c247', 'a f c23'])
fn('_space', ['f'], ['c31 _c23 +8', 'space +1 c31', 'a f space'])
vars('''\
! _space +1
( _space +8
, +4 (
H +32 (
W _c23 +64''')
fn('_d', ['f'], ['` _space +64', 'd +4 `', 'a f d'])
vars('''\
e _d +1
l _d +8
co +3 l''')
fn('group1', ['halfout'], [
'out halfout halfout',
'out out H',
'out out e',
'out out l',
'out out l',
'out out co',
'out out ,',
'out _space out'])
fn('halfout', ['self', 'char'], ['a o char', 'a self self'])
vars('''\
out group1 halfout
r +3 co
out out W
out out co
out out r
out out l
out _d out
out out !''')
fn('main', ['x'], [])
__import__("sys").stdout.write(program)
EOF
python3 grassy.py > result
cat result
echo
cat result | wc -c
ruby /opt/grass/grass.rb result
Locksmith:
import re
code = """\
72 $ .
28 + $ $ 1 + .
8 + $ .  $ $ .
3 + $ .
44 .
32 .
87 .
$ .
3 + .
.
.
33 .
"""
lookup = {"+": 1, "_": 2, "*": 3, ",": 8, ".": 9, "$": 70, "dec": 71, "dig": 72, "len": 74, "rev": 75, "range": 76, "pop": 77, "sign": 78, "=": 79}
def codify(word):
	word = word.group()
	if word in lookup: return `lookup[word]`
	return "0" + word[0] + "".join("0%s71" % d for d in word[1:])
result = re.sub(r"\s+", "", re.sub(r"\w+|[^ \r\n\t\v]", codify, code))
print len(result)
print(result)
Whirl:
import re

op = "_ # 1 0 ; : p m & ? , ."
math = "_ ; : + * / 0 < > = ! -"
opi = 0
mathi = 0
opd = 1
mathd = 1
isop = True

code = """\
1 _ : ; _ + _ + _ + _ : _ + _ : _ * _ + _ : . _
    : ; _ + _ + _ + _ + _ : _ + _ : _ * : + _ : . _ :
          + _ + _ + _ + _ + _ + _ + _ : . _ . _ :
          + _ + _ + _ : . _
    : ; _ + _ + _ + _ + _ : _ + : + _ : _ + _ : _ + _ : . _
    : ; _ + _ : _ + _ : _ + _ : _ + _ : _ + _ : . _
    : ; _ + _ + _ + _ + _ + _ + _ : _ + _ + _ : _ + _ : _ + : + _ + _ + _ : . _
    : ; _ + _ + _ : _ + _ + _ : _ + _ + _ + : + _ : _ + _ + _ : . _ :
          + _ + _ + _ : . - :
          + _ + _ + _ + _ + _ + _ - _ : . - :
          + _ + _ + _ + _ + _ + _ + _ + _ - _ : . _
    : ; _ + _ : _ + _ : _ + _ : _ + _ : _ + : + _ : ."""
# i'm using 1 letter per line. most are just simple +1 or x2

result = ""

for tok in re.split("\\s+", code):
	curr = 0
	dir = 0
	try:
		if isop:
			curr = opi
			next = op.index(tok) // 2
			dir = opd
		else:
			curr = mathi
			next = math.index(tok) // 2
			dir = mathd
	except:
		raise BaseException("Command %s not found on %s ring" % (tok, "operation" if isop else "math"))
	delta = (next - curr) % 12
	if delta > 6 and dir == 1:
		dir = -1
		result += "0"
	if delta and delta < 6 and dir == -1:
		dir = 1
		result += "0"
	if delta and dir == -1:
		delta = 12 - delta
	result += "1" * delta + "00" 
	if isop:
		opi = next
		opd = dir
	else:
		mathi = next
		mathd = dir
	isop = not isop

print len(result)
print result

Probably optimal:
A Pear Tree
Cubically
Incident
MarioLANG
Monkeys
Functoid

Almost certainly optimal:
4
Dodos
Swap

Wrong:
HBCHT

Broken:
BrainFlump
Gaot++

Incomplete:
Ceres

Warns:
ELF (x86/x64, Linux)
-->

## Table of Contents


 - [,,,, 14 bytes](#-14-bytes)
 - [///, 13 bytes](#-13-bytes)
 - [05AB1E, 7 bytes](#05ab1e-7-bytes)
 - [2sable, 7 bytes](#2sable-7-bytes)
 - [3var, 65 bytes](#3var-65-bytes)
 - [4, 117 bytes](#4-117-bytes)
 - [7, 17 bytes](#7-17-bytes)
 - [99, 283 bytes](#99-283-bytes)
 - [;#+, 106 bytes](#-106-bytes)
 - [><>, 23 bytes](#-23-bytes)
 - [???, 80 bytes](#-80-bytes)
 - [\\/, 189 bytes](#-189-bytes)
 - [A Pear Tree, 27 bytes](#a-pear-tree-27-bytes)
 - [_Acc!!_, 122 bytes](#acc-122-bytes)
 - [Aceto, 19 bytes](#aceto-19-bytes)
 - [Actually, 1 byte](#actually-1-byte)
 - [Ada (GNAT), 54 bytes](#ada-gnat-54-bytes)
 - [Add++, 16 bytes](#add-16-bytes)
 - [ADJUST, 281 bytes](#adjust-281-bytes)
 - [Agda, 48 bytes](#agda-48-bytes)
 - [Agony, 33 bytes](#agony-33-bytes)
 - [Aheui (esotope), 145 bytes](#aheui-esotope-145-bytes)
 - [ALGOL 68 (Genie), 33 bytes](#algol-68-genie-33-bytes)
 - [Alice, 22 bytes](#alice-22-bytes)
 - [Alice ML, 46 bytes](#alice-ml-46-bytes)
 - [AlphaBeta, 68 bytes](#alphabeta-68-bytes)
 - [Alphuck, 76 bytes](#alphuck-76-bytes)
 - [Alumin, 108 bytes](#alumin-108-bytes)
 - [anyfix, 15 bytes](#anyfix-15-bytes)
 - [APL (Dyalog Classic), 17 bytes](#apl-dyalog-classic-17-bytes)
 - [APL (Dyalog Unicode), 17 bytes](#apl-dyalog-unicode-17-bytes)
 - [APL (ngn/apl), 17 bytes](#apl-ngn-apl-17-bytes)
 - [Appleseed, 46 bytes](#appleseed-46-bytes)
 - [ARBLE, 15 bytes](#arble-15-bytes)
 - [Archway, 366 bytes](#archway-366-bytes)
 - [Archway2, 182 bytes](#archway2-182-bytes)
 - [Arcyóu, 15 bytes](#arcyóu-15-bytes)
 - [ArnoldC, 71 bytes](#arnoldc-71-bytes)
 - [AsciiDots, 18 bytes](#asciidots-18-bytes)
 - [ASPeRiX, 16 bytes](#asperix-16-bytes)
 - [Assembly (as, x64, Linux), 64 bytes](#assembly-as-x64-linux-64-bytes)
 - [Assembly (fasm, x64, Linux), 119 bytes](#assembly-fasm-x64-linux-119-bytes)
 - [Assembly (gcc, x64, Linux), 150 bytes](#assembly-gcc-x64-linux-150-bytes)
 - [Assembly (JWasm, x64, Linux), 120 bytes](#assembly-jwasm-x64-linux-120-bytes)
 - [Assembly (MIPS, SPIM), 73 bytes](#assembly-mips-spim-73-bytes)
 - [Assembly (nasm, x64, Linux), 117 bytes](#assembly-nasm-x64-linux-117-bytes)
 - [Attache, 21 bytes](#attache-21-bytes)
 - [Aubergine, 29 bytes](#aubergine-29-bytes)
 - [AWK, 25 bytes](#awk-25-bytes)
 - [axo, 29 bytes](#axo-29-bytes)
 - [Bash, 18 bytes](#bash-18-bytes)
 - [bc, 16 bytes](#bc-16-bytes)
 - [Beam, 120 bytes](#beam-120-bytes)
 - [Bean, 17 bytes](#bean-17-bytes)
 - [BeanShell, 23 bytes](#beanshell-23-bytes)
 - [Beatnik, 117 bytes](#beatnik-117-bytes)
 - [Beeswax, 15 bytes](#beeswax-15-bytes)
 - [Befunge-93, 21 bytes](#befunge-93-21-bytes)
 - [Befunge-93 (FBBI), 21 bytes](#befunge-93-fbbi-21-bytes)
 - [Befunge-93 (MTFI), 21 bytes](#befunge-93-mtfi-21-bytes)
 - [Befunge-93 (PyFunge), 21 bytes](#befunge-93-pyfunge-21-bytes)
 - [Befunge-96 (MTFI), 21 bytes](#befunge-96-mtfi-21-bytes)
 - [Befunge-97 (MTFI), 21 bytes](#befunge-97-mtfi-21-bytes)
 - [Befunge-98 (FBBI), 18 bytes](#befunge-98-fbbi-18-bytes)
 - [Befunge-98 (PyFunge), 19 bytes](#befunge-98-pyfunge-19-bytes)
 - [Binary Lambda Calculus, 14 bytes](#binary-lambda-calculus-14-bytes)
 - [BitBitJump, 130 bytes](#bitbitjump-130-bytes)
 - [BitChanger, 379 bytes](#bitchanger-379-bytes)
 - [Bitwise, 149 bytes](#bitwise-149-bytes)
 - [Bitwise Fuckery, 96 bytes](#bitwise-fuckery-96-bytes)
 - [Black (blak), INVALID](#black-blak-invalid)
 - [Boo, 20 bytes](#boo-20-bytes)
 - [Boolfuck, 155 bytes](#boolfuck-155-bytes)
 - [Brachylog, 16 bytes](#brachylog-16-bytes)
 - [Brachylog v1, 3 bytes](#brachylog-v1-3-bytes)
 - [Braille, 57 bytes](#braille-57-bytes)
 - [Brain-Flak, 136 bytes](#brain-flak-136-bytes)
 - [Brain-Flak (BrainHack), 136 bytes](#brain-flak-brainhack-136-bytes)
 - [Brainbash, 78 bytes](#brainbash-78-bytes)
 - [brainbool, 157 bytes](#brainbool-157-bytes)
 - [BrainFlump, 362 bytes](#brainflump-362-bytes)
 - [brainfuck, 76 bytes](#brainfuck-76-bytes)
 - [Braingolf, 17 bytes](#braingolf-17-bytes)
 - [Brat, 17 bytes](#brat-17-bytes)
 - [Broccoli, 22 bytes](#broccoli-22-bytes)
 - [Brian & Chuck, 32 bytes](#brian--chuck-32-bytes)
 - [Bubblegum, 11 bytes](#bubblegum-11-bytes)
 - [C (clang), 30 bytes](#c-clang-30-bytes)
 - [C (gcc), 30 bytes](#c-gcc-30-bytes)
 - [C (tcc), 30 bytes](#c-tcc-30-bytes)
 - [C# (.NET Core), 67 bytes](#c-net-core-67-bytes)
 - [C# (Mono C# compiler), 67 bytes](#c-mono-c-compiler-67-bytes)
 - [C# (Mono C# Shell), 30 bytes](#c-mono-c-shell-30-bytes)
 - [C# (Visual C# Compiler), 67 bytes](#c-visual-c-compiler-67-bytes)
 - [C# (Visual C# Interactive Compiler), 30 bytes](#c-visual-c-interactive-compiler-30-bytes)
 - [C++ (clang), 51 bytes](#c-clang-51-bytes)
 - [C++ (gcc), 47 bytes](#c-gcc-47-bytes)
 - [Cardinal, 18 bytes](#cardinal-18-bytes)
 - [Cauliflower, 18 bytes](#cauliflower-18-bytes)
 - [Ceres, 34 bytes](#ceres-34-bytes)
 - [Ceylon, 42 bytes](#ceylon-42-bytes)
 - [Chain, 13 bytes](#chain-13-bytes)
 - [Changeling, 90 bytes](#changeling-90-bytes)
 - [Chapel, 23 bytes](#chapel-23-bytes)
 - [Charcoal, 13 bytes](#charcoal-13-bytes)
 - [Charm, 25 bytes](#charm-25-bytes)
 - [Check, 16 bytes](#check-16-bytes)
 - [Cheddar, 20 bytes](#cheddar-20-bytes)
 - [Chef, 236 bytes](#chef-236-bytes)
 - [Chez Scheme, 24 bytes](#chez-scheme-24-bytes)
 - [CHICKEN Scheme, 22 bytes](#chicken-scheme-22-bytes)
 - [Chip, 97 bytes](#chip-97-bytes)
 - [CIL (Mono IL assembler), 121 bytes](#cil-mono-il-assembler-121-bytes)
 - [Cinnamon Gum, 15 bytes](#cinnamon-gum-15-bytes)
 - [cixl, 26 bytes](#cixl-26-bytes)
 - [CJam, 15 bytes](#cjam-15-bytes)
 - [Clean, 33 bytes](#clean-33-bytes)
 - [CLIPS, 29 bytes](#clips-29-bytes)
 - [Clojure, 22 bytes](#clojure-22-bytes)
 - [COBOL (GNU), 56 bytes](#cobol-gnu-56-bytes)
 - [Cobra, 40 bytes](#cobra-40-bytes)
 - [Coconut, 22 bytes](#coconut-22-bytes)
 - [CoffeeScript 1, 28 bytes](#coffeescript-1-28-bytes)
 - [CoffeeScript 2, 28 bytes](#coffeescript-2-28-bytes)
 - [Commentator, 197 bytes](#commentator-197-bytes)
 - [Commercial, 83 bytes](#commercial-83-bytes)
 - [Common Lisp, 22 bytes](#common-lisp-22-bytes)
 - [Condit, 41 bytes](#condit-41-bytes)
 - [Convex, 14 bytes](#convex-14-bytes)
 - [Cood, 381 bytes](#cood-381-bytes)
 - [Corea, 13 bytes](#corea-13-bytes)
 - [COW, 261 bytes](#cow-261-bytes)
 - [cQuents 0, 15 bytes](#cquents-0-15-bytes)
 - [Crayon, 16 bytes](#crayon-16-bytes)
 - [Crystal, 20 bytes](#crystal-20-bytes)
 - [CSL, 81 bytes](#csl-81-bytes)
 - [Cubically, 78 bytes](#cubically-78-bytes)
 - [Cubix, 29 bytes](#cubix-29-bytes)
 - [Curry (Sloth), 37 bytes](#curry-sloth-37-bytes)
 - [Cy, 18 bytes](#cy-18-bytes)
 - [D, 52 bytes](#d-52-bytes)
 - [D2, 22 bytes](#d2-22-bytes)
 - [Dash, 18 bytes](#dash-18-bytes)
 - [dc, 16 bytes](#dc-16-bytes)
 - [Deadfish~, 1 byte](#deadfish-1-byte)
 - [Decimal, 45 bytes](#decimal-45-bytes)
 - [Del\|m\|t, 30 bytes](#delmt-30-bytes)
 - [Deorst, 15 bytes](#deorst-15-bytes)
 - [Detour, 19 bytes](#detour-19-bytes)
 - [Dirty, 16 bytes](#dirty-16-bytes)
 - [DOBELA, 123 bytes](#dobela-123-bytes)
 - [Dodos, 159 bytes](#dodos-159-bytes)
 - [Dreaderef, 31 bytes](#dreaderef-31-bytes)
 - [DStack, 21 bytes](#dstack-21-bytes)
 - [eacal, 24 bytes](#eacal-24-bytes)
 - [ecpp + C (gcc), 30 bytes](#ecpp-c-gcc-30-bytes)
 - [ecpp + C++ (gcc), 51 bytes](#ecpp-c-gcc-51-bytes)
 - [Egel, 52 bytes](#egel-52-bytes)
 - [Element, 17 bytes](#element-17-bytes)
 - [ELF (x86/x64, Linux), 59 bytes](#elf-x86x64-linux-59-bytes)
 - [Elixir, 22 bytes](#elixir-22-bytes)
 - [ELVM-IR, 66 bytes](#elvm-ir-66-bytes)
 - [Emacs Lisp, 22 bytes](#emacs-lisp-22-bytes)
 - [Emmental, 57 bytes](#emmental-57-bytes)
 - [Emoji, 24 bytes](#emoji-24-bytes)
 - [Emojicode, 37 bytes](#emojicode-37-bytes)
 - [Emotinomicon, 30 bytes](#emotinomicon-30-bytes)
 - [Enlist, 15 bytes](#enlist-15-bytes)
 - [Erlang (escript), 37 bytes](#erlang-escript-37-bytes)
 - [ETA, 73 bytes](#eta-73-bytes)
 - [evil, 70 bytes](#evil-70-bytes)
 - [Explode, 68 bytes](#explode-68-bytes)
 - [ExtraC, 37 bytes](#extrac-37-bytes)
 - [F# (.NET Core), 21 bytes](#f-net-core-21-bytes)
 - [F# (Mono), 21 bytes](#f-mono-21-bytes)
 - [face, 41 bytes](#face-41-bytes)
 - [Factor, 28 bytes](#factor-28-bytes)
 - [Fantom, 43 bytes](#fantom-43-bytes)
 - [Felix, 21 bytes](#felix-21-bytes)
 - [FerNANDo, 109 bytes](#fernando-109-bytes)
 - [FEU, 15 bytes](#feu-15-bytes)
 - [Fireball, 14 bytes](#fireball-14-bytes)
 - [fish, 18 bytes](#fish-18-bytes)
 - [Fission, 17 bytes](#fission-17-bytes)
 - [Fission 2, 17 bytes](#fission-2-17-bytes)
 - [Flipbit, 148 bytes](#flipbit-148-bytes)
 - [FOCAL-69, 20 bytes](#focal-69-20-bytes)
 - [Foo, 14 bytes](#foo-14-bytes)
 - [Forked, 42 bytes](#forked-42-bytes)
 - [Forte, 25 bytes](#forte-25-bytes)
 - [Forth (gforth), 17 bytes](#forth-gforth-17-bytes)
 - [Fortran (GFortran), 28 bytes](#fortran-gfortran-28-bytes)
 - [Fourier, 15 bytes](#fourier-15-bytes)
 - [FRACTRAN, 86 bytes](#fractran-86-bytes)
 - [Fueue, 40 bytes](#fueue-40-bytes)
 - [Funciton, 209 bytes](#funciton-209-bytes)
 - [Functoid, 53 byes](#functoid-53-bytes)
 - [Funky, 20 bytes](#funky-20-bytes)
 - [Gaia, 14 bytes](#gaia-14-bytes)
 - [Gambit Scheme (gsi), 22 bytes](#gambit-scheme-gsi-22-bytes)
 - [Gaot++, 679 bytes](#gaot-679-bytes)
 - [GAP, 23 bytes](#gap-23-bytes)
 - [Glypho, 456 bytes](#glypho-456-bytes)
 - [Glypho (shorthand), 114 bytes](#glypho-shorthand-114-bytes)
 - [gnuplot, 31 bytes](#gnuplot-31-bytes)
 - [Go, 61 bytes](#go-61-bytes)
 - [Gol><>, 16 chars](#gol-16-chars)
 - [GolfScript, 15 btyes](#golfscript-15-btyes)
 - [Grass, 448 bytes](#grass-448-bytes)
 - [Grime, 2 bytes](#grime-2-bytes)
 - [Groovy, 20 bytes](#groovy-20-bytes)
 - [GS2, 2 bytes](#gs2-2-bytes)
 - [Guile, 24 bytes](#guile-24-bytes)
 - [Half-Broken Car in Heavy Traffic, (3201 bytes)](#half-broken-car-in-heavy-traffic-3201-bytes)
 - [Haskell, 26 bytes](#haskell-26-bytes)
 - [Haxe, 61 bytes](#haxe-61-bytes)
 - [Haystack, 17 bytes](#haystack-17-bytes)
 - [Hexadecimal Stacking Pseudo-Assembly Language, 162 bytes](#hexadecimal-stacking-pseudo-assembly-language-162-bytes)
 - [Hexagony, 29 bytes](#hexagony-29-bytes)
 - [Hodor, 28 bytes](#hodor-28-bytes)
 - [Huginn, 31 bytes](#huginn-31-bytes)
 - [Husk, 8 bytes](#husk-8-bytes)
 - [Hyper-Dimensional Brainfuck, 76 bytes](#hyper-dimensional-brainfuck-76-bytes)
 - [I, INVALID](#i-invalid)
 - [Icon, 43 bytes](#icon-43-bytes)
 - [Idris, 36 bytes](#idris-36-bytes)
 - [Implicit, 14 bytes](#implicit-14-bytes)
 - [Incident, 2080 bytes](#incident-2080-bytes)
 - [INTERCAL, 246 bytes](#intercal-246-bytes)
 - [Io, 20 bytes](#io-20-bytes)
 - [J, 19 bytes](#j-19-bytes)
 - [J-uby, 19 bytes](#j-uby-19-bytes)
 - [Japt, 12 bytes](#japt-12-bytes)
 - [Java (OpenJDK 8), 76 bytes](#java-openjdk-8-76-bytes)
 - [Java (JDK 10), 76 bytes](#java-jdk-10-76-bytes)
 - [JavaScript (Babel Node), 28 bytes](#javascript-babel-node-28-bytes)
 - [JavaScript (Node.js), 28 bytes](#javascript-nodejs-28-bytes)
 - [JavaScript (SpiderMonkey), 20 bytes](#javascript-spidermonkey-20-bytes)
 - [Jelly, 8 bytes](#jelly-8-bytes)
 - [Jellyfish, 15 bytes](#jellyfish-15-bytes)
 - [Joy, 29 bytes](#joy-29-bytes)
 - [jq, 15 bytes](#jq-15-bytes)
 - [Julia 0.4, 22 bytes](#julia-04-22-bytes)
 - [Julia 0.5, 22 bytes](#julia-05-22-bytes)
 - [Julia 0.6, 22 bytes](#julia-06-22-bytes)
 - [Jx, 19 bytes](#jx-19-bytes)
 - [K (Kona), 18 bytes](#k-kona-18-bytes)
 - [K (oK), 20 bytes](#k-ok-20-bytes)
 - [K (ngn/k), 18 bytes](#k-ngn-k-18-bytes)
 - [kavod, 44 bytes](#kavod-44-bytes)
 - [Klein, 16 bytes](#klein-16-bytes)
 - [Kotlin, 49 bytes](#kotlin-49-bytes)
 - [ksh, 18 bytes](#ksh-18-bytes)
 - [Labyrinth, 40 bytes](#labyrinth-40-bytes)
 - [Lean, 21 bytes](#lean-21-bytes)
 - [Lily, 33 bytes](#lily-33-bytes)
 - [Literate Haskell, 27 bytes](#literate-haskell-27-bytes)
 - [LLVM IR, 110 bytes](#llvm-ir-110-bytes)
 - [LNUSP, 349 bytes](#lnusp-349-bytes)
 - [Locksmith, 79 bytes](#locksmith-79-bytes)
 - [Logicode, 109 bytes](#logicode-109-bytes)
 - [LOLCODE, 37 bytes](#lolcode-37-bytes)
 - [Lost, 45 bytes](#lost-45-bytes)
 - [LOWER, 177 bytes](#lower-177-bytes)
 - [Lua, 20 bytes](#lua-20-bytes)
 - [Ly, 17 bytes](#ly-17-bytes)
 - [M, 14 bytes](#m-14-bytes)
 - [M4, 13 bytes](#m4-13-bytes)
 - [MachineCode, 54 bytes](#machinecode-54-bytes)
 - [Make, 27 bytes](#make-27-bytes)
 - [Malbolge, 112 bytes](#malbolge-112-bytes)
 - [MarioLANG, 235 bytes](#mariolang-235-bytes)
 - [Mascarpone, 29 bytes](#mascarpone-29-bytes)
 - [Mathics, 21 bytes](#mathics-21-bytes)
 - [MATL, 15 bytes](#matl-15-bytes)
 - [Maverick, 45 bytes](#maverick-45-bytes)
 - [Maxima, 23 bytes](#maxima-23-bytes)
 - [MaybeLater, 20 bytes](#maybelater-20-bytes)
 - [Milky Way, 16 bytes](#milky-way-16-bytes)
 - [Minimal-2D, 123 bytes](#minimal-2d-123-bytes)
 - [miniML, 26 bytes](#miniml-26-bytes)
 - [Minkolang, 18 bytes](#minkolang-18-bytes)
 - [Mirror, 16 bytes](#mirror-16-bytes)
 - [Momema, 63 bytes](#momema-63-bytes)
 - [Monkeys, 448 bytes](#monkeys-448-bytes)
 - [Moonscript, 20 bytes](#moonscript-20-bytes)
 - [Mornington Crescent, 3568 bytes](#mornington-crescent-3568-bytes)
 - [MUMPS, 18 bytes](#mumps-18-bytes)
 - [MY, 60 bytes](#my-60-bytes)
 - [MY-BASIC, 20 bytes](#my-basic-20-bytes)
 - [Neim, 16 bytes](#neim-16-bytes)
 - [Neutrino, 15 bytes](#neutrino-15-bytes)
 - [Nhohnhehr, 181 bytes](#nhohnhehr-181-bytes)
 - [Nim, 19 bytes](#nim-19-bytes)
 - [NotQuiteThere, 17 bytes](#notquitethere-17-bytes)
 - [NTFJ (NTFJC), 106 bytes](#ntfj-ntfjc-106-bytes)
 - [Numberwang, 72 bytes](#numberwang-72-bytes)
 - [Oasis, 14 bytes](#oasis-14-bytes)
 - [Objective-C (clang), 30 bytes](#objective-c-clang-30-bytes)
 - [Objective-C (gcc), 30 bytes](#objective-c-gcc-30-bytes)
 - [OCaml, 27 bytes](#ocaml-27-bytes)
 - [occam-pi, 83 bytes](#occam-pi-83-bytes)
 - [Octave, 19 bytes](#octave-19-bytes)
 - [Ohm, 14 bytes](#ohm-14-bytes)
 - [Ohm v2, 14 bytes](#ohm-v2-14-bytes)
 - [OML, 16 bytes](#oml-16-bytes)
 - [oOo CODE, 228 bytes](#ooo-code-228-bytes)
 - [ORK, 80 bytes](#ork-80-bytes)
 - [OSH, 18 bytes](#osh-18-bytes)
 - [Paradoc, 2 bytes](#paradoc-2-bytes)
 - [Parenthetic, 604 bytes](#parenthetic-604-bytes)
 - [Pain-Flak, 152 bytes](#pain-flak-152-bytes)
 - [Pari/GP, 22 bytes](#parigp-22-bytes)
 - [Pascal (FPC), 32 bytes](#pascal-fpc-32-bytes)
 - [PATH, 113 bytes](#path-113-bytes)
 - [pbrain, 87 bytes](#pbrain-87-bytes)
 - [Perl 5, 18 bytes](#perl-5-18-bytes)
 - [Perl 6, 19 bytes](#perl-6-19-bytes)
 - [Phoenix, 20 bytes](#phoenix-20-bytes)
 - [Phooey, 14 bytes](#phooey-14-bytes)
 - [PHP, 13 bytes](#php-13-bytes)
 - [PicoLisp, 26 bytes](#picolisp-26-bytes)
 - [Piet, 183 bytes](#piet-183-bytes)
 - [Pike, 35 bytes](#pike-35-bytes)
 - [PingPong, 30 bytes](#pingpong-30-bytes)
 - [Pip, 15 bytes](#pip-15-bytes)
 - [pl, 13 bytes](#pl-13-bytes)
 - [Pony, 62 bytes](#pony-62-bytes)
 - [Positron, 21 bytes](#positron-21-bytes)
 - [PostL, 16 bytes](#postl-16-bytes)
 - [PostScript (xpost), 21 bytes](#postscript-xpost-21-bytes)
 - [PowerShell, 15 bytes](#powershell-15-bytes)
 - [PowerShell Core, 15 bytes](#powershell-core-15-bytes)
 - [Prelude, 38 bytes](#prelude-38-bytes)
 - [Premier, 14 bytes](#premier-14-bytes)
 - [Preproc, 13 bytes](#preproc-13-bytes)
 - [Prolog (Ciao), 29 bytes](#prolog-ciao-29-bytes)
 - [Prolog (SWI), 25 bytes](#prolog-swi-25-bytes)
 - [Proton, 22 bytes](#proton-22-bytes)
 - [Proton 2.0, 21 bytes](#proton-2-0-21-bytes)
 - [Pure, 33 bytes](#pure-33-bytes)
 - [PureScript, 79 bytes](#purescript-79-bytes)
 - [Purple, 62 bytes](#purple-62-bytes)
 - [Pushy, 16 bytes](#pushy-16-bytes)
 - [Pyke, 14 bytes](#pyke-14-bytes)
 - [Pylons, 16 bytes](#pylons-16-bytes)
 - [Pyon, 20 bytes](#pyon-20-bytes)
 - [Pyramid Scheme, 857 bytes](#pyramid-scheme-857-bytes)
 - [Pyt, 40 bytes](#pyt-40-bytes)
 - [Pyth, 14 bytes](#pyth-14-bytes)
 - [Python 1, 20 bytes](#python-1-20-bytes)
 - [Python 2, 20 bytes](#python-2-20-bytes)
 - [Python 2 (Cython), 20 bytes](#python-2-cython-20-bytes)
 - [Python 2 (IronPython), 20 bytes](#python-2-ironpython-20-bytes)
 - [Python 2 (Jython), 20 bytes](#python-2-jython-20-bytes)
 - [Python 2 (PyPy), 20 bytes](#python-2-pypy-20-bytes)
 - [Python 3, 22 bytes](#python-3-22-bytes)
 - [Python 3 (Cython), 22 bytes](#python-3-cython-22-bytes)
 - [Python 3 (Stackless), 22 bytes](#python-3-stackless-22-bytes)
 - [QuadR, 13 bytes](#quadr-13-bytes)
 - [Quadrefunge-97 (MTFI), 21 bytes](#quadrefunge-97-mtfi-21-bytes)
 - [QuadS, 13 bytes](#quads-13-bytes)
 - [Quarterstaff, 43 bytes](#quarterstaff-43-bytes)
 - [Quintefunge-97 (MTFI), 21 bytes](#quintefunge-97-mtfi-21-bytes)
 - [R, 20 bytes](#r-20-bytes)
 - [Racket, 37 bytes](#racket-37-bytes)
 - [Rail, 27 bytes](#rail-27-bytes)
 - [Random Brainfuck, 76 bytes](#random-brainfuck-76-bytes)
 - [Rapira, 22 bytes](#rapira-22-bytes)
 - [Recursiva, 14 bytes](#recursiva-14-bytes)
 - [Reason, 23 bytes](#reason-23-bytes)
 - [Red, 25 bytes](#red-25-bytes)
 - [Reng, 20 bytes](#reng-20-bytes)
 - [ReRegex, 13 bytes](#reregex-13-bytes)
 - [Reticular, 17 bytes](#reticular-17-bytes)
 - [Retina, 14 bytes](#retina-14-bytes)
 - [Retina 0.8.2, 14 bytes](#retina-0-8-2-14-bytes)
 - [Rexx (Regina), 18 bytes](#rexx-regina-18-bytes)
 - [rk, 37 bytes](#rk-37-bytes)
 - [ROOP, 17 bytes](#roop-17-bytes)
 - [Rotor, 14 bytes](#rotor-14-bytes)
 - [RProgN, 14 bytes](#rprogn-14-bytes)
 - [RProgN 2, 15 bytes](#rprogn-2-15-bytes)
 - [Ruby, 19 bytes](#ruby-19-bytes)
 - [Rust, 34 bytes](#rust-34-bytes)
 - [Röda, 23 bytes](#röda-23-bytes)
 - [S.I.L.O.S, 19 bytes](#silos-19-bytes)
 - [Sad-Flak, 199 bytes](#sad-flak-199-bytes)
 - [Sakura, 1 byte](#sakura-1-byte)
 - [Scala, 47 bytes](#scala-47-bytes)
 - [sed, 14 bytes](#sed-14-bytes)
 - [sed 4.2.2, 19 bytes](#sed-422-19-bytes)
 - [Seed, 4203 bytes](#seed-4203-bytes)
 - [Self-modifying Brainfuck, 29 bytes](#self-modifying-brainfuck-29-bytes)
 - [Septefunge-97 (MTFI), 21 bytes](#septefunge-97-mtfi-21-bytes)
 - [Seriously, 1 byte](#seriously-1-byte)
 - [Sesos, 21 bytes](#sesos-21-bytes)
 - [Set, 84 bytes](#set-84-bytes)
 - [Sexefunge-97 (MTFI), 21 bytes](#sexefunge-97-mtfi-21-bytes)
 - [Shakespeare Programming Language, 612 bytes](#shakespeare-programming-language-612-bytes)
 - [ShapeScript, 15 bytes](#shapescript-15-bytes)
 - [shortC, 16 bytes](#shortc-16-bytes)
 - [Shove, 16 bytes](#shove-16-bytes)
 - [Shtriped, 239 bytes](#shtriped-239-bytes)
 - [Shnap, 22 bytes](#shnap-22-bytes)
 - [Sidef, 18 bytes](#sidef-18-bytes)
 - [Simplefunge, 57 bytes](#simplefunge-57-bytes)
 - [Simula (cim), 24 bytes](#simula-cim-24-bytes)
 - [SISAL, INVALID](#sisal-invalid)
 - [Snails, INVALID](#snails-invalid)
 - [SNOBOL4 (CSNOBOL4), 28 bytes](#snobol4-csnobol4-28-bytes)
 - [Snowman, 18 bytes](#snowman-18-bytes)
 - [SNUSP (Modular), 291 bytes](#snusp-modular-291-bytes)
 - [SNUSP (Snuspi), 45 bytes](#snusp-snuspi-45-bytes)
 - [Somme, 38 bytes](#somme-38-bytes)
 - [Spaced, 67 bytes](#spaced-67-bytes)
 - [SQLite, 21 bytes](#sqlite-21-bytes)
 - [Squirrel, 22 bytes](#squirrel-22-bytes)
 - [Stack Cats, 134 bytes](#stack-cats-134-bytes)
 - [Stacked, 18 bytes](#stacked-18-bytes)
 - [Standard ML (MLton), 21 bytes](#standard-ml-mlton-21-bytes)
 - [Starry, 169 bytes](#starry-169-bytes)
 - [Stax, 8 bytes](#stax-8-bytes)
 - [Stencil, 1 byte](#stencil-1-byte)
 - [Stones, 647 bytes](#stones-647-bytes)
 - [str, 17 bytes](#str-17-bytes)
 - [Straw, 2 bytes](#straw-2-bytes)
 - [Subskin, 47 bytes](#subskin-47-bytes)
 - [Surface, 516 bytes](#surface-516-bytes)
 - [Swap, 29 bytes](#swap-29-bytes)
 - [Swift 4, 22 bytes](#swift-4-22-bytes)
 - [Symbolic Brainfuck, 182 bytes](#symbolic-brainfuck-182-bytes)
 - [Symbolic Python, 200 bytes](#symbolic-python-200-bytes)
 - [Syms, 16 bytes](#syms-16-bytes)
 - [TacO, 16 bytes](#taco-16-bytes)
 - [Tampio (functional), INVALID](#tampio-functional-invalid)
 - [Tampio (imperative), 46 bytes](#tampio-imperative-46-bytes)
 - [Taxi, 183 bytes](#taxi-183-bytes)
 - [Tcl, 19 bytes](#tcl-19-bytes)
 - [tcsh, 18 bytes](#tcsh-18-bytes)
 - [TemplAt, 37 bytes](#templat-37-bytes)
 - [Templates Considered Harmful, 50 bytes](#templates-considered-harmful-50-bytes)
 - [Threead, 16 bytes](#threead-16-bytes)
 - [Thue, 25 bytes](#thue-25-bytes)
 - [Thutu, 20 bytes](#thutu-20-bytes)
 - [TinCan, 532 bytes](#tincan-532-bytes)
 - [tinyBF, 105 bytes](#tinybf-105-bytes)
 - [tinylisp, 41 bytes](#tinylisp-41-bytes)
 - [TIS, 170 bytes](#tis-170-bytes)
 - [TRANSCRIPT, 36 bytes](#transcript-36-bytes)
 - [Trefunge-97 (MTFI), 21 bytes](#trefunge-97-mtfi-21-bytes)
 - [Trefunge-98 (PyFunge), 19 bytes](#trefunge-98-pyfunge-19-bytes)
 - [Triangular, 66 bytes](#triangular-66-bytes)
 - [Triangularity, 49 bytes](#triangularity-49-bytes)
 - [Trigger, 40 bytes](#trigger-40-bytes)
 - [TrumpScript, 36 bytes](#trumpscript-36-bytes)
 - [Turtlèd, 14 bytes](#turtlèd-14-bytes)
 - [TypeScript, 28 bytes](#typescript-28-bytes)
 - [uBASIC, 17 bytes](#ubasic-17-bytes)
 - [Underload, 16 bytes](#underload-16-bytes)
 - [Unefunge-97 (MTFI), 21 bytes](#unefunge-97-mtfi-21-bytes)
 - [Unefunge-98 (PyFunge), 19 bytes](#unefunge-98-pyfunge-19-bytes)
 - [Unicat, 832 bytes](#unicat-832-bytes)
 - [Unlambda, 36 bytes](#unlambda-36-bytes)
 - [Unreadable, 577 bytes](#unreadable-577-bytes)
 - [V, 14 bytes](#v-14-bytes)
 - [Vala, 36 bytes](#vala-36-bytes)
 - [VAR, 19 bytes](#var-19-bytes)
 - [Verbosity, 390 bytes](#verbosity-390-bytes)
 - [Visual Basic .NET (.NET Core), 67 bytes](#visual-basic-net-net-core-67-bytes)
 - [Visual Basic .NET (Mono), 67 bytes](#visual-basic-net-mono-67-bytes)
 - [Vitsy, 16 bytes](#vitsy-16-bytes)
 - [VSL, 32 bytes](#vsl-32-bytes)
 - [Whirl, 955 bytes](#whirl-955-bytes)
 - [Whispers v1, 29 bytes](#whispers-v1-29-bytes)
 - [Whispers v2, 29 bytes](#whispers-v2-29-bytes)
 - [Whitespace, 146 bytes](#whitespace-146-bytes)
 - [Width, 30 bytes](#width-30-bytes)
 - [Wierd (John's), 181 bytes](#wierd-johns-181-bytes)
 - [Wise, 135 bytes](#wise-135-bytes)
 - [Woefully (WARNING: INCORRECT)](#woefully-warning-incorrect)
 - [Wolfram Language (Mathematica), 21 bytes](#wolfram-language-mathematica-21-bytes)
 - [wsf, 174 bytes](#wsf-174-bytes)
 - [Wumpus, 19 bytes](#wumpus-19-bytes)
 - [xEec, 64 bytes](#xeec-64-bytes)
 - [xeraph, 19 bytes](#xeraph-19-bytes)
 - [YABALL, 368 bytes](#yaball-368-bytes)
 - [Yabasic, 16 bytes](#yabasic-16-bytes)
 - [yash, 18 bytes](#yash-18-bytes)
 - [yup, 1171 bytes](#yup-1171-bytes)
 - [Zephyr, 20 bytes](#zephyr-20-bytes)
 - [Zig, 81 bytes](#zig-81-bytes)
 - [zkl, 22 bytes](#zkl-22-bytes)
 - [Zsh, 17 bytes](#zsh-17-bytes)

## [,,,](https://github.com/totallyhuman/commata), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##S87PzU0sSfz/X8kjNScnX0chPL8oJ0Xx/38A)
## [///](https://esolangs.org/wiki////), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##K85JLM5ILf7/3yM1JydfRyE8vygnRfH/fwA)
## [05AB1E](https://github.com/Adriandmen/05AB1E), 7 bytes
```
”Ÿ™,‚ï!
```
[Try it online!](https://tio.run/##MzBNTDJM/f//UcPcozsetSzSedQw6/B6xf//AQ)
## [2sable](https://github.com/Adriandmen/2sable), 7 bytes
```
”Ÿ™,‚ï!
```
[Try it online!](https://tio.run/##MypOTMpJ/f//UcPcozsetSzSedQw6/B6xf//AQ)
## [3var](https://esolangs.org/wiki/3var), 65 bytes
```
iiisa-<*>P/>is+iP>PPm-iiiPi<O/<m/>+<O+d<+<O+><kkkOP->siskkkOP</>P
```
[Try it online!](https://tio.run/##Hcg7CsAwEAPR@8SYLdIKXcG6giGNMGmykOtvPs3wmP2eV5XtnB0bFXQ2i9LZ3ytjBM5gw2gHvhJrraHOdP5CUFUP)
## [4](https://github.com/urielieli/py-four), 117 bytes
```
3.6000160103602136033260433605446067260787008070200908000120902111120111011015065095105105115055035075115125105085044
```
[Try it online!](https://tio.run/##HYuJCcBAEAI7CrP/pf/CNl5EZBTM3XgasMaIxk0R4U2GqDKbHtU5A4fB4RXo4gI3yVFwXXTxlvFbtYoo5rL5HTlF5u4H)
## [7](https://esolangs.org/wiki/7), 17 bytes
```
5325101303040432004513151401430134321027403
```
[Try it online!](https://tio.run/##DcmxEQAwDAKxlR6DL/tPRtxKr13PChkT4oGsrFVQfHEm5gW3Hw)
## [99](https://github.com/TryItOnline/99), 283 bytes
```
999 9 9
99 99999999 999 9
99
99 99999 9 999 9
99
99 99 999 999999
99
99
99 9999999 9999 999 9
99
99 99 9999999 9 999 9 999 9 999 9
99
99 99 999999 9 999999 9
99
9999
99 99999 999 999999 999 9
99
99 9999999 9999 9 999 9
99
99 99 999999 9
99
99 99 999999 999 9
99
99 99999 9999999 9
99
```
[Try it online!](https://tio.run/##s7T8/9/S0lIBCLlAFBQogDFQBC6ogC6mYAlXz2WJohRKY1GPbJACLkPh4khSKA5BUobuSrjVuMzFFMH0KJLa//8B)
## [;#+](https://github.com/ConorOBrien-Foxx/shp), 106 bytes
```
;;;;;;;;;~++++++++>#<+++;;:>#<+-;;>#<#<-;;;>#<-+++++++;;;;-:>#<-+;;;#::<;;;-++#:<#<;;;#-<;;;#<+;;#-:<-+;;#
```
[Try it online!](https://tio.run/##NYvBDcAwDAKH4Wl5AWx1njwr5Z/VXWOlPOCEYK@3Kn4du3qQ7REUeEQHslPgd6ODc4omkKnCDOytGh9PE3JWqPoA)
## [><>](https://esolangs.org/wiki/Fish), 23 bytes
```
"!dlroW ,olleH"l?!;oe0.
```
[Try it online!](https://tio.run/##S8sszvj/X0kxJacoP1xBJz8nJ9VDKcde0To/1UDv/38A)
## [???](https://github.com/ararslan/qqq-lang), 80 bytes
```
;,".."-..;,;...;...--'",,,,;."----!----,!-!!--.!----!;;!;;;,!-!...!;;!;,!-----.!
```
[Try it online!](https://tio.run/##HUqxDQAwCLpFly7IA1zl/4NFCRABu3tGSDKLFES7VfUShtwbsYao8MELIZnazu@XcIP3mQ8)
## [\\/](https://github.com/TryItOnline/v-fmota), 189 bytes
```
\/>>>\/\\/>\/\\/>\/\\>\>\\>\[/\/>>>>\[/\/\>>>\[/\/\>>>>\\/>>\/\>>>/\//\//>\/\]/\//>\/\]/\//\/>>>\]/\/\\\\./\/\\/>>\/\\/>\/\./\/\\./\/\./\/>\>>>>\>>>\./\/>\\/>>\/\\[/\/\\/>\/\./\//\//\/\]/\/
```
[Try it online!](https://tio.run/##VU0xEoAwCHuR8oN8pDi4uPVcPL@PhFyvtg0hUEjf7er3c0a4AXDzzJORN9GsXiX8L8BJSGeLYHUsQtaUnmc3@c9v1CkmQcYMlWO42bIilG/EBw)
## [A Pear Tree](https://esolangs.org/wiki/A_Pear_Tree), 27 bytes
```
#r3TQJ
print"Hello, World!"
```
[Try it online!](https://tio.run/##S9QtSE0s0i0pSk39/1@5yDgk0IuroCgzr0TJIzUnJ19HITy/KCdFUen/fwA)
## [_Acc!!_](https://github.com/dloscutoff/Esolangs/tree/master/Acc!!), 122 bytes
```
108
Write 72
Write 101
Write _
Write _
Write 111
Write 44
Write 32
Write 87
Write 111
Write 114
Write _
Write 100
Write 33
```
[Try it online!](https://tio.run/##S0xOTkr6/9/QwIIrvCizJFXB3AjKMDQwhLLi0WhDQ5iMiQmUYQzTZWGOocjQ0ATdAAMDmD7j//8B)
## [Aceto](https://github.com/aceto/aceto), 19 bytes
```
o,or
l Wl
le!d
"H"p
```
[Try it online!](https://tio.run/##S0xOLcn//z9fJ7@IK0chPIcrJ1UxhUvJQ6ng/38A)
## [Actually](https://github.com/Mego/Seriously), 1 byte
```
H
```
[Try it online!](https://tio.run/##S0wuKU3Myan8/9/j/38A)
## [Ada (GNAT)](https://www.gnu.org/software/gnat/), 54 bytes
```
procedure GNAT.IO.H is begin Put("Hello, World!");end;
```
[Try it online!](https://tio.run/##S0xJ1E3PSyz5/7@gKD85NaW0KFXB3c8xRM/TX89DIbNYISk1PTNPIaC0REPJIzUnJ19HITy/KCdFUUnTOjUvxfr/fwA)
## [Add++](https://github.com/SatansSon/AddPlusPlus), 16 bytes
```
L,"Hello, World!
```
[Try it online!](https://tio.run/##S0xJKSj4/99HR8kjNScnX0chPL8oJ0Xx//9/@QUlmfl5xf91MwE)
## [ADJUST](https://github.com/TryItOnline/adjust), 281 bytes
```
 ;I-      &  e$      &  m-        &  g2Ph$      &  a2$      &  n$      &  e2+-      &  g2Ph$      &  OPh$      &  m-      &  e-      &  n-
}     AgR};      AgR};      A=AgR};         AgR};       AgR};      AgR};        AgR};         AgR};        AgR};      AgR};      AgR};      AC
```
[Try it online!](https://tio.run/##S0zJKi0u@f9fwdpTVwEM1BQUUlXgzFyoKJiTbhSQgZBKNEKw8xDMVCNtXRw6/JE5uUj2IZh5uly1YLZjelCttQIG0xaJgyqFQwcaB6cUDqbz//8A)
## [Agda](http://wiki.portal.chalmers.se/agda), 48 bytes
```
open import IO
main = run(putStr"Hello, World!")
```
[Try it online!](https://tio.run/##S0xPSfz/P78gNU8hM7cgv6hEwdOfKzcxM0/BVqGoNE@joLQkuKRIySM1JydfRyE8vygnRVFJ8/9/AA)
## [Agony](https://github.com/royvanrijn/JAgony), 33 bytes
```
<[.<]$$$,{}~<~)+{~*@+{${)~*~)~)~@<-
```
[Try it online!](https://tio.run/##S0zPz6v8/98mWs8mVkVFRae6ts6mTlO7uk7LQbtapVqzTqtOEwgdbHT//wcA)
## [Aheui (esotope)](https://github.com/aheui/pyaheui), 145 bytes
```
발따밤따빠받나파빠밣다빠밦다빠받타밢밢따밦다밤밣따밦밦따빠밣다파받따빠받다파빠빠밠타밣밢따아멓희 
```
[Try it online!](https://tio.run/##S8xILc38///1hjmvp2x4vWEJiNy54PWG2a@bZrzt6QGzF7/uXgJmLIMxZr9tbni9YREIgXSBxYF6gSohXCCCmgPSCzIHaCDcZIgIkA3iLgAbtRhi1JupLa9XTn47d43C//8A)
## [ALGOL 68 (Genie)](https://jmvdveer.home.xs4all.nl/algol.html), 33 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##S8xJz88xs0j//7@gKDOvREPJIzUnJ19HITy/KCdFUUnz/38A)
## [Alice](https://github.com/m-ender/alice), 22 bytes
```
/OH!lloo /
@""edlr,W\ 
```
[Try it online!](https://tio.run/##S8zJTE79/1/f30MxJyc/X0Gfy0FJKTUlp0gnPEbh/38A)
## [Alice ML](https://github.com/aliceml/aliceml), 46 bytes
```
print"Hello, World!";
val _=OS.Process.exit 0;
```
[Try it online!](https://tio.run/##S8zJTE7Nzfn/v6AoM69EySM1JydfRyE8vygnRVHJmqssMUch3tY/WC@gKD85tbhYL7Uis0TBwPr/fwA)
## [AlphaBeta](https://github.com/TryItOnline/alphabeta), 68 bytes
```
kjjjggDLeaCLcbbbCLLaaaCLjjjggDLjhhDLsFihhDLCLaaaCLdaaaaCLdaaCLsFiiDL
```
[Try it online!](https://tio.run/##NYnBDYAwDMSGS8TrlrhA1TTwqAT7h1aFly2bV3daeZh5RkStikLBbmYCkMO/HO6Ke2sTss7BHzJPU2S@)
## [Alphuck](https://github.com/TryItOnline/tio-transpilers), 76 bytes
```
epepaaaeccccseaiaiaaaeaeesaajaeejaeejjeeejaaeejaiiijccjcjeeejiiiiiijcijcciij
```
[Try it online!](https://tio.run/##HYhBCgAxDALfKiJsbA@Bsu9P0ygyKnZ@P1eVUglAbB0h2r0gHcCNifXKrIgwac4VI/NdzaoL)
## [Alumin](https://github.com/ConorOBrien-Foxx/Alumin), 108 bytes
```
hhdtdadhatdoddhhhgahhhhhadohhhhhhhadodohhhadoydhhgddhhdtdaaohhhhcoyhhhhhddaaaoydohhhadohhhdacdohhdtdacohhhco
```
[Try it online!](https://tio.run/##PcvBCsAwCAPQbw0GmsI2L@2hX@9U2LwkyAuufc8nQuIiKCw6KWlAdaBLX@ueeRKMUrVBA/PTivlAAv@3hFUWNW8Z8QI)
## [anyfix](https://github.com/alexander-liao/anyfix), 15 bytes
```
“Hello, World!”
```
[Try it online!](https://tio.run/##S8yrTMus@P//UcMcj9ScnHwdhfD8opwUxUcNc///BwA)
## [APL (Dyalog Classic)](https://www.dyalog.com/), 17 bytes
```
⎕←'Hello, World!'
```
[Try it online!](https://tio.run/##SyzI0U2pTMzJT9dNzkksLs5M/v//Ud/UR20T1D1Sc3LydRTC84tyUhTV//8HAA)
## [APL (Dyalog Unicode)](https://www.dyalog.com/), 17 bytes
```
⎕←'Hello, World!'
```
[Try it online!](https://tio.run/##SyzI0U2pTMzJT////1Hf1EdtE9Q9UnNy8nUUwvOLclIU1f//BwA)
## [APL (ngn/apl)](https://github.com/ngn/apl), 17 bytes
```
⎕←'Hello, World!'
```
[Try it online!](https://tio.run/##SyzI0c1Lz/v//1Hf1EdtE9Q9UnNy8nUUwvOLclIU1f//BwA)
## [Appleseed](https://github.com/dloscutoff/appleseed), 46 bytes
```
(def start!(lambda(_)(write!"Hello, World!")))
```
[Try it online!](https://tio.run/##SywoyEktTk1N@f9fIyU1TaG4JLGoRFEjJzE3KSVRI15To7wosyRVUckjNScnX0chPL8oJ0VRSVNT8/9/AA)
## [ARBLE](https://github.com/TehFlaminTaco/ARBLE), 15 bytes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##SyxKykn9/1/JIzUnJ19HITy/KCdFUen/fwA)
## [Archway](https://github.com/TryItOnline/archway), 366 bytes
```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.+++++++++++++++++++++++++++++.+++++++..+++.-------------------------------------------------------------------.------------.+++++++++++++++++++++++++++++++++++++++++++++++++++++++.++++++++++++++++++++++++.+++.------.--------.-------------------------------------------------------------------.
```

[Try it online!](https://tio.run/##SyxKzihPrPz/X5tKQI8oWT0QQ0@XcoBihh613YzkSj2sNpLr6v//AQ)
## [Archway2](https://github.com/TryItOnline/archway), 182 bytes
```
                   \
 /
  >++>+++>+++>+<<<<-/>+>+>->+<<<<<-\>>.>---.+++++++..+++.>>++++.------------.<-.<.+++.------.--------.>>+.
  \    \
\++++>
++++++++/                         /
```
[Try it online!](https://tio.run/##dY07CoBADET7PUX6kASslzlJGrGxthFPH7PuooL4mMDkP2/Lus/HFEFfvJAVIjCnRtREDOkgPavigEJElDvajAKXlxdaU/pU72Yb1nzl/a23TZRxjo3@sIgT)
## [Arcyóu](https://github.com/Nazek42/arcyou), 15 bytes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##SyxKrswv/f9fySM1JydfRyE8vygnRVHp/38A)
## [ArnoldC](https://lhartikk.github.io/ArnoldC/), 71 bytes
```
IT'S SHOWTIME
TALK TO THE HAND "Hello, World!"
YOU HAVE BEEN TERMINATED
```
[Try it online!](https://tio.run/##DcmxCoAgEADQ3a@4XFr6CcMDpVTIK2mMbDsS/H@4euu7@tu43iKexgzZpUI@oCKzLkAJyCE4Ey1o9zC3CUrrXAetzrT/cSDMiBEIt@CjIbQiHw)
## [AsciiDots](https://github.com/aaronduino/asciidots), 18 bytes
```
.-$"Hello, World!"
```
[Try it online!](https://tio.run/##SyxOzsxMyS8p/v9fT1dFySM1JydfRyE8vygnRVHp/38A)
## [ASPeRiX](https://github.com/TryItOnline/asperix), 16 bytes
```
"Hello, World!".
```
[Try it online!](https://tio.run/##SywuSC3KrPj/X8kjNScnX0chPL8oJ0VRSe///3/5BSWZ@XnF/3ULSzNTSwA)
## [Assembly (as, x64, Linux)](https://sourceware.org/binutils/docs/as/index.html), 64 bytes
```
.globl _start
.print "Hello, World!"
_start:mov $60,%rax
syscall
```
[Try it online!](https://tio.run/##Jck9DkBAEAbQfk@xhM6KSuEEbqCUWX@RfIzsbITLGxLteyQybR63I1EtF7CH7SVSiKY8wrpHm7YTwIXtOGBMUvNvs/Fps7oq8kCXkVsGAlSfYQYtoq7b2X3yAg)
## [Assembly (fasm, x64, Linux)](https://flatassembler.net/), 119 bytes
```
format ELF executable
mov eax,4
mov ebx,1
mov ecx,s
mov edx,13
int 128
mov eax,1
mov ebx,0
int 128
s db "Hello, World!"
```
[Try it online!](https://tio.run/##SywuTs1NyqnUTUsszv3/Py2/KDexRMHVx00htSI1ubQkMSknlSs3v0whNbFCxwTCSqrQMYSwkit0iiGsFKCYMVdmXomCoZEFXIMhXIMBXK5YISVJQckjNScnX0chPL8oJ0VR6f9/AA)
## [Assembly (gcc, x64, Linux)](https://gcc.gnu.org/), 150 bytes
```
.data
s:.string "Hello, World!"
.globl main
main:movl $4,%eax
movl $1,%ebx
movl $s,%ecx
movl $13,%edx
int $128
movl $1,%eax
movl $0,%ebx
int $128
ret

```
[Try it online!](https://tio.run/##SywuTs1NyqnUTU9O/v9fLyWxJJGr2EqvuKQoMy9dQckjNScnX0chPL8oJ0VRiUsvPSc/KUchNzEzjwtEWOXml@UoqJjoqKYmVnBBOIZAThKMUwzkJMNljIG8lAquzLwSIMfIAkkDXLcBRDdcSVFqCdf//wA)
## [Assembly (JWasm, x64, Linux)](https://github.com/JWasm/JWasm), 120 bytes
```
.code
mov eax,4
mov ebx,1
lea ecx,s
mov edx,13
int 128
s db"Hello, World!"
end
```
[Try it online!](https://tio.run/##SywuTs1NyqnUzSpPLM79/18vOT8llSu@uCSxqMQqN79MITWxQseEC8xKqtAx5MpJTVRITa7QKYaIpQDFjLky80oUDI0suGAaDOEaDOByxQopSUoeqTk5@ToK4flFOSmKSlypeSkKELv@/wcA)
## [Assembly (MIPS, SPIM)](https://github.com/TryItOnline/spim), 73 bytes
```
.data
s:.ascii"Hello, World!"
.text
main:la$a0,s
syscall
li$v0,10
syscall
```
[Try it online!](https://tio.run/##Ky7IzP3/Xy8lsSSRq9hKL7E4OTNTySM1JydfRyE8vygnRVGJS68ktaKEKzcxM88qJ1El0UCnmKu4sjg5MSeHKydTpcxAx9AAJvD/PwA)
## [Assembly (nasm, x64, Linux)](http://www.nasm.us/), 117 bytes
```
global _start
_start:mov edx,13
mov ecx,s
mov eax,4
mov ebx,1
int 128
mov eax,1
mov ebx,0
int 128
s db"Hello, World!"
```
[Try it online!](https://tio.run/##PclBCoAgEEDRvaeYWhtktYhO0A1axpgSwZjQSNjpLRJc/Q8Pma3T9DQnsktpJ6@RYOWAVxA5k/M3WBOl6sW/W5ScD6Mc8umPxXEGUN1YTBVrizEYXc@WyEtY/EWmqlN6AQ)
## [Attache](https://github.com/ConorOBrien-Foxx/attache), 21 bytes
```
Print!"Hello, World!"
```
[Try it online!](https://tio.run/##SywpSUzOSP3/P6AoM69EUckjNScnX0chPL8oJ0VR6f9/AA)
## [Aubergine](https://esolangs.org/wiki/Aubergine), 29 bytes
```
-a1=oA-a1:bA=iB!dlroW ,olleH
```
[Try it online!](https://tio.run/##SyxNSi1Kz8xL/f9fN9HQNt8RSFolOdpmOjEopuQU5Ycr6OTn5KR6/P8PAA)
## [AWK](https://www.gnu.org/software/gawk/manual/gawk.html), 25 bytes
```
END{print"Hello, World!"}
```
[Try it online!](https://tio.run/##SyzP/v/f1c@luqAoM69EySM1JydfRyE8vygnRVGp9v9/AA)
## [axo](https://esolangs.org/wiki/Axo), 29 bytes
```
"!dlroW ,o%
\%#[<"Hell<
 >( ^
```
[Try it online!](https://tio.run/##S6zI//9fSTElpyg/XEEnX5UrRlU52kbJIzUnx4ZLwU5DIe7/fwA)
## [Bash](https://www.gnu.org/software/bash/), 18 bytes
```
echo Hello, World!
```
[Try it online!](https://tio.run/##S0oszvj/PzU5I1/BIzUnJ19HITy/KCdF8f9/AA)
## [bc](https://www.gnu.org/software/bc/manual/html_mono/bc.html), 16 bytes
```
"Hello, World!"

```
[Try it online!](https://tio.run/##S0r@/1/JIzUnJ19HITy/KCdFUYnr/38A)
## [Beam](https://github.com/ETHproductions/beam-js), 120 bytes
```
'''''''''>`++++++++)@'''P''''>`++++)+@+++++++@P@+++@'P'L'''>`++++++)''P'>`++++)@''p@'p>`+++++)@'p@+++@`p@--------@''p+@H
```
[Try it online!](https://tio.run/##S0pNzP3/Xx0G7BK0oUDTAcgNQIhpajtAZRwCQCwHoKQPkg5NkGqoUqDWAgf1AqgUkFsA1pFQ4KALBSAV2g4e//8DAA)
## [Bean](https://github.com/patrickroberts/bean), 17 bytes
```
00000000: 2623 8100 c8e5 ecec efac a0d7 eff2 ece4  &#..............
00000010: 21                                       !
```
[Try it online!](https://tio.run/##S0pNzPv/3wAKrBSMzIyMFSwMDQwUki1STRVSk1OTFVLTEpMVEg1SzIGsNCOQmImCgpqyHgrggphgCDLDUIE4oPj/PwA)
## [BeanShell](http://www.beanshell.org/), 23 bytes
```
print("Hello, World!");
```
[Try it online!](https://tio.run/##S0pNzCvOSM3J@f@/oCgzr0RDyQPIyddRCM8vyklRVNK0/v8fAA)
## [Beatnik](https://esolangs.org/wiki/Beatnik), 117 bytes
```
k zzzc xw xw z k xx k x k d k k k zzxa k zzzzzzzzf xw k zd z xw xo k k k x xw k zk k zzzzzzzzzzxx qs z xo xw xj kd xo
```
[Try it online!](https://tio.run/##TYtdCoAwDIOvkqtNp6AFhyhYcvnazD3YNv3jy7SU@9gswkByhj8qwuCulqopJemljy9WgXnWpOVqA/Pxtx@bVsd5iWwd3mE194gX)
## [Beeswax](https://github.com/m-lohmann/BeeswaxEsolang.jl), 15 bytes
```
_`Hello, World!
```
[Try it online!](https://tio.run/##S0pNLS5PrPj/Pz7BIzUnJ19HITy/KCdF8f9/AA)
## [Befunge-93](https://github.com/catseye/Befunge-93), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##S0pNK81LT/3/X0kxJacoP1xBJz8nJ9VDyc5KWSfe4f9/AA)
## [Befunge-93 (FBBI)](https://github.com/catseye/FBBI), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##S0pNK81LT9W1NNZNS0rK/P9fSTElpyg/XEEnPycn1UPJzkpZJ97h/38A)
## [Befunge-93 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##S0pNK81LT9W1NNbNLUnL/P9fSTElpyg/XEEnPycn1UPJzkpZJ97h/38A)
## [Befunge-93 (PyFunge)](https://github.com/catseye/Befunge-93), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##S0pNK81LT9W1NNYtqAQz//9XUkzJKcoPV9DJz8lJ9VCys1LWiXf4/x8A)
## [Befunge-96 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##S0pNK81LT9W1NNPNLUnL/P9fSTElpyg/XEEnPycn1UPJzkpZJ97h/38A)
## [Befunge-97 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 18 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##S0pNK81LT9W1NNfNLUnL/P9fSTElpyg/XEEnPycn1UPJzkpZJ97h/38A)
## [Befunge-98 (FBBI)](https://github.com/catseye/FBBI), 19 bytes
```
"ck,@!dlroW ,olleH
```
[Try it online!](https://tio.run/##S0pNK81LT9W1tPj/Xyk5W8dBMSWnKD9cQSc/JyfV4/9/AA)
## [Befunge-98 (PyFunge)](https://pythonhosted.org/PyFunge/), 19 bytes
```
"!dlroW ,olleH"ck,@
```
[Try it online!](https://tio.run/##S0pNK81LT9W1tNAtqAQz//9XUkzJKcoPV9DJz8lJ9VBKztZx@P8fAA)
## [Binary Lambda Calculus](https://tromp.github.io/cl/cl.html), 14 bytes
```
00000000: 2a48 656c 6c6f 2c20 576f 726c 6421       *Hello, World!
```
[Try it online!](https://tio.run/##S8pJ/v/fAAqsFIwSTSwUzEzNkhXMks3SFIySjQwUTM2BLHMjkJiJkaECBGh5pObk5OsohOcX5aQo/v8PAA)
## [BitBitJump](https://github.com/TryItOnline/bitbitjump), 130 bytes
```
Z0:0Z1:0
.deref i c
.testH c p-1
p:.out c
.next i
0 0 0
c:0i:s
s:72 101 108
108 111 44
32 87 111
114 108 100
33-1
.include lib.bbj
```
[Try it online!](https://tio.run/##HYxBCsMwDATveoU@UCPFhgS9oG/I0Y4LCmlqahn6e8cpyxx2FjaqRbW9vUvvKwmtLARuy9/8QsUEznK1JyYsD4Yi7tPstmf@GSoQjkASUqlQZZ6QiQcLDJCZMQTwEy7zXYA54H8gAu/HodMzHW3LeGh0Me69Xw)
## [BitChanger](https://github.com/TryItOnline/bitchanger), 379 bytes
```
<<<<<}<<<<}<<<}<<<}}<}}<}}<}}<}}}<}}}}<}}<<<<<<<<<<<}}<}}<}}<}}<}}<}}<}}}<}}<}}<<<<<<<<<<<}<}}<}}<}}<}}<}}<}}<}}<}}<}}}<<<<<<<<<<<}}<}}<}}<}}}<}}<}}<}}<}}}<<<<<<<<<<<}}<}}<}}<}}<}}<}}<}}}<<<<<<<<<}}<}}<}}<}}}}}<}}}}<<<<<<<<<<<}}<}}<}}<}}<}}}}<<<<<<<<}}<}}<}}<}}<}}<}}}}}<}}<<<<<<<<<<<}}<}}<}}<}}<}}<}}}}}<<<<<<<<<<}}<}}<}}<}}<}}<}}<}}<<<<<<<<}}<}}<}}<}}}<}}<}}<}}}<}}<<<<<<<<<<<}
```
[Try it online!](https://tio.run/##S8osSc5IzEtPLfr/3wYEamEEGNciIzAGsxEAVQVCHZoqrOpgqrGaRowaLPLIgjAH49KLkMI0kKA/UQzG6jV8fkI3/f9/AA)
## [Bitwise](https://github.com/aaronryank/bitwise), 149 bytes
```
MOV 1 &1 &1
OUT &72 1
OUT &101 1
OUT &108 1
OUT &108 1
OUT &111 1
OUT &44 1
OUT &32 1
OUT &87 1
OUT &111 1
OUT &114 1
OUT &108 1
OUT &100 1
OUT &33 1
```
[Try it online!](https://tio.run/##S8osKc8sTv3/39c/TMFQQQ2EuPxDQxTUzI0UoCxDA0ME0wIb0xCuwMQExjKG67cwx6LQ0NAEq6EGcP3GCob//wMA)
## [Bitwise Fuckery](https://github.com/cairdcoinheringaahing/Bitwise-Fuckery), 96 bytes
```{%raw%}
+>+>+@+{{{+{{{.&+{+{{{+{{+.+++++++..+++.<+{{+{+{{.&+{{{{{.<+{{+{{+{+{+.<.+++.------.--------.<+.
{%endraw%}```
[Try it online!](https://tio.run/##SypPK03OTi2q/P9f2w4IHbSrq6tBWE9NuxrK1tbThgA9EEPPBiQEEgcpAQGoCFgQKA1WpAsGUArIsNHW@/8fAA)
## [Black (blak)](https://github.com/TryItOnline/blak), INVALID
## [Boo](http://boo-lang.org/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##S8rP//@/oCgzr0TJIzUnJ19HITy/KCdFUen/fwA)
## [Boolfuck](https://github.com/TryItOnline/boolfuck), 155 bytes
```
;;;+;+;;+;+;+;+;+;+;;+;;+;;;+;;+;+;;+;;;+;;+;+;;+;+;;;;+;+;;+;;;+;;+;+;+;;;;;;;+;+;;+;;;+;+;+;+;+;+;;;;+;+;;+;;+;+;;+;;;+;;;+;;+;+;;+;;;+;+;;+;;+;+;+;;;;+;
```
[Try it online!](https://tio.run/##S8rPz0krTc7@/9/a2lobCMEEDEIRTBiNDeJhiIMFUcWRzLNGMhahD42vjWqYtvX//wA)
## [Brachylog](https://github.com/JCumin/Brachylog), 16 bytes
```
"Hello, World!"w
```
[Try it online!](https://tio.run/##SypKTM6ozMlPN/r/X8kjNScnX0chPL8oJ0VRqfz/fwA)
## [Brachylog v1](https://github.com/JCumin/Brachylog/releases), 3 bytes
```
@Hw
```
[Try it online!](https://tio.run/##SypKTM6ozMlP///fwaP8/38A)
## [Braille](https://gist.github.com/threeifbywhiskey/0e98d42150eb644a3406), 57 bytes
```
⠆⠄⡒⡆⡘⠀⠊⠦⢦⠗⢾⠽⠂⢢⢾⢦⢦⠮⢄
```
[Try it online!](https://tio.run/##JcixCYAwFEXRWRUshFROICGksLTR8uUVKd1Ah7mLfBG7wxmXYU5pikAVFdpOq7QTrWhDHXd04AfdKGN/9v8XLhEv)
## [Brain-Flak](https://github.com/DJMcMayhem/Brain-Flak), 148 bytes
```
((((((((((((()()){}){}){}){}()))){}{}())([][]){})[][])[[]]())[((()[]){}){}])([()[]](([]([](((([][]))([]{}{})))[]{}[])[[]])))(([][][]){})
```
[Try it online!](https://tio.run/##TYzBCoAwDEN/pzvsI/yOksM8CKJ48Dr27TVZRSyFNmle17vtV93OdkTYv4qV0sfXVNJzMYdD9pzuAE0Xk3YfYEYKxqzaLCGx@sJnWl6cKu/JR0RdHg)
## [Brain-Flak (BrainHack)](https://github.com/Flakheads/BrainHack), 148 bytes
```
((((((((((((()()){}){}){}){}()))){}{}())([][]){})[][])[[]]())[((()[]){}){}])([()[]](([]([](((([][]))([]{}{})))[]{}[])[[]])))(([][][]){})
```
[Try it online!](https://tio.run/##TYwxDoAwDAO/4w48gndEGVoWEBIDa9W3B7tBiChSYseXdtfj2ut2RuBfBaX08TWV9Fxgbi57TjN3miYm7T6cGSkHs2ogIbH6wmdaXpwq78lHxLI@)
## [Brainbash](https://github.com/ConorOBrien-Foxx/Brainbash), 78 bytes
```
-[++[<++>->+++>+++<<]---->+]<<<<.<<<<-.<..<<+.<<<<.>>.>>>-.<.+++.>>.>-.<<<<<+.
```
[Try it online!](https://tio.run/##HUqxDcAwDDoI2RcgHokyJFO7dGj/l0uMMALDftf97PVdVTGAQUAhWH3kDEOYNPJIJNMGHVIydX5ed4ou3Ff9)
## [brainbool](https://github.com/TryItOnline/tio-transpilers), 157 bytes
```
.+.+..+.+....+..+..+.+.+.+.+..+.+..+...+..+.+..+...+..+.+....+..+.+.+..+....+.+......+.+.+.+.+...+.+..+.+....+.+...+..+.+..+..+.+..+...+..+..+.+....+.+....+.
```
[Try it online!](https://tio.run/##SypKzMxLys/P@f9fTxsIIYQehAXmaCOJa@vpYWUjKYZxwRSKCWjmo5mFaiaqMiDx//9/XScA)
## [BrainFlump](https://github.com/gunnerwolf/BrainFlump), 362 bytes
```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.+++++++++++++++++++++++++++++.+++++++:..+++.-------------------------------------------------------------------.------------.+++++++++++++++++++++++++++++++++++++++++++++++++++++++.++++++++++++++++++++++++.+++.;.--------.-------------------------------------------------------------------.
```
[Try it online!](https://tio.run/##SypKzMxLyynNLfj/X5tKQI8oWSs9EEtPl3KAYoYetR0NdqW1HlbLyHXw//8A)
## [brainfuck](https://github.com/TryItOnline/tio-transpilers), 78 bytes
```
+[+[<<<+>>>>]+<-<-<<<+<++]<<.<++.<++..+++.<<++.<---.>>.>.+++.------.>-.>>--.
```
[Try it online!](https://tio.run/##HYhRCoBAEEIPJOMJZC6y7EcFQQR9BJ1/ckeRp@7vdj3nd9xVGBiSkNaEwvYSMCUaHWKVXhHBTGZf0WKuy6z6AQ)
## [Braingolf](https://github.com/gunnerwolf/braingolf), 17 bytes
```
"Hello, World!"&@
```
[Try it online!](https://tio.run/##SypKzMxLz89J@/9fySM1JydfRyE8vygnRVFJzeH/fwA)
## [Brian & Chuck](https://github.com/m-ender/brian-chuck), 32 bytes
```
_#Jgnnq."Yqtnf#_{?
#{<{>-?>--.>?
```
[Try it online!](https://tio.run/##SyrKTMzTTc4oTc7@/z9e2Ss9L69QTymysCQvTTm@2p5Ludqm2k7X3k5XV8/O/v9/AA)
## [Brat](https://github.com/presidentbeef/brat), 17 bytes
```
p "Hello, World!"
```
[Try it online!](https://tio.run/##SypKLPn/v0BBySM1JydfRyE8vygnRVHp/38A)
## [Broccoli](https://github.com/broccoli-lang/broccoli), 22 bytes
```
(print"Hello, World!")
```
[Try it online!](https://tio.run/##SyrKT07Oz8n8/1@joCgzr0TJIzUnJ19HITy/KCdFUUnz/38A)
## [Bubblegum](https://esolangs.org/wiki/Bubblegum), 11 bytes
```
00000000: 1527 4d50 62a9 9a29 6b6d e2              .'MPb..)km.
```
[Try it online!](https://tio.run/##SypNSspJTS/N/f/fwMrQ1MjcJMXUwMwo0dIy0cjSLMksJdXo/38A)
## [C (clang)](http://clang.llvm.org/), 30 bytes
```
main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##S9ZNzknMS///PzcxM09Ds7qgtKRYQ8kjNScnX0chPL8oJ0VRSdO69v//f8lpOYnpxf91w/PydRNzcgA)
## [C (gcc)](https://gcc.gnu.org/), 30 bytes
```
main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##S9ZNT07@/z83MTNPQ7O6oLSkWEPJIzUnJ19HITy/KCdFUUnTuvb//3/JaTmJ6cX/dcPz8nUTc3IA)
## [C (tcc)](http://savannah.nongnu.org/projects/tinycc), 30 bytes
```
main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##S9YtSU7@/z83MTNPQ7O6oLSkWEPJIzUnJ19HITy/KCdFUUnTuvb//3/JaTmJ6cX/dcPz8nUTc3IA)
## [C# (.NET Core)](https://www.microsoft.com/net/core/platform), 67 bytes
```
class H{static void Main(){System.Console.Write("Hello, World!");}}
```
[Try it online!](https://tio.run/##Sy7WTc4vSv3/PzknsbhYwaO6uCSxJDNZoSw/M0XBNzEzT0OzOriyuCQ1V885P684PydVL7wosyRVQ8kjNScnX0chPL8oJ0VRSdO6tvb/fwA)
## [C# (Mono C# compiler)](http://www.mono-project.com/), 67 bytes
```
class H{static void Main(){System.Console.Write("Hello, World!");}}
```
[Try it online!](https://tio.run/##Sy7Wzc3Py///PzknsbhYwaO6uCSxJDNZoSw/M0XBNzEzT0OzOriyuCQ1V885P684PydVL7wosyRVQ8kjNScnX0chPL8oJ0VRSdO6tvb/fwA)
## [C# (Mono C# Shell)](http://www.mono-project.com/docs/tools+libraries/tools/repl/), 30 bytes
```
Console.Write("Hello, World!")
```
[Try it online!](https://tio.run/##Sy7Wzc3Py9ctzkjNyfn/3zk/rzg/J1UvvCizJFVDyQMomK@jEJ5flJOiqKT5/z8A)
## [C# (Visual C# Compiler)](http://www.mono-project.com/docs/about-mono/releases/5.0.0/#csc), 67 bytes
```
class H{static void Main(){System.Console.Write("Hello, World!");}}
```
[Try it online!](https://tio.run/##Sy7WTS5O/v8/OSexuFjBo7q4JLEkM1mhLD8zRcE3MTNPQ7M6uLK4JDVXzzk/rzg/J1UvvCizJFVDySM1JydfRyE8vygnRVFJ07q29v9/AA)
## [C# (Visual C# Interactive Compiler](http://www.mono-project.com/docs/about-mono/releases/5.0.0/#csc)
```
Console.Write("Hello, World!")
```
[Try it online!](https://tio.run/##Sy7WTS7O/P/fOT@vOD8nVS@8KLMkVUPJIzUnJ19HITy/KCdFUUnz/38A)
## [C++ (clang)](http://clang.llvm.org/), 51 bytes
```
#include<cstdio>
int main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##Sy4o0E3OScxL//9fOTMvOac0JdUmubgkJTPfjiszr0QhNzEzT0OzuqC0pFhDySM1JydfRyE8vygnRVFJ07r2/38A)
## [C++ (gcc)](https://gcc.gnu.org/), 47 bytes
```
#include<cstdio>
main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##Sy4o0E1PTv7/XzkzLzmnNCXVJrm4JCUz344rNzEzT0OzuqC0pFhDySM1JydfRyE8vygnRVFJ07r2/38A)
## [Cardinal](https://www.esolangs.org/wiki/Cardinal), 18 bytes
```
%"Hello, World!";x
```
[Try it online!](https://tio.run/##S04sSsnMS8z5/19VySM1JydfRyE8vygnRVHJuuL/fwA)
## [Cauliflower](https://github.com/broccoli-lang/broccoli), 18 bytes
```
(p"Hello, World!")
```
[Try it online!](https://tio.run/##S04szclMy8kvTy36/1@jQMkjNScnX0chPL8oJ0VRSfP/fwA)
## [Ceres](https://github.com/alexander-liao/ceres), 34 bytes
```
389960998265612367812323333 115dÆP
```
[Try it online!](https://tio.run/##S04tSi3@/9/YwtLSzMDS0sLIzNTM0MjYzNwCSBoZA4GCoaFpyuG2gP//AQ)
## [Ceylon](https://ceylon-lang.org/), 42 bytes
```
shared void run(){print("Hello, World!");}
```
[Try it online!](https://tio.run/##S06tzMnP@/@/OCOxKDVFoSw/M0WhqDRPQ7O6oCgzr0RDySM1JydfRyE8vygnRVFJ07r2/38A)
## [Chain](https://github.com/ConorOBrien-Foxx/Chain), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##S85IzMz7/98jNScnX0chPL8oJ0Xx/38A)
## [Changeling](https://github.com/DennisMitchell/shapescript), 90 bytes
```
"IpQ:AQ  
""2(-znK]
"" "Tr4r[
"")$dNcA 
"" #!&   
         
         
         
         

```
[Try it online!](https://tio.run/##S85IzEtPzcnMS///X8mzINDKMVBBgUtJyUhDtyrPOxbIUlAKKTIpigayNFVS/JIdQbIKyopqCkB1CjBAgPX/PwA)
## [Chapel](http://chapel.cray.com/), 23 bytes
```
write("Hello, World!");
```
[Try it online!](https://tio.run/##S85ILEjN@f@/vCizJFVDySM1JydfRyE8vygnRVFJ0/r/fwA)
## [Charcoal](https://github.com/somebody1234/Charcoal), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##S85ILErOT8z5/98jNScnX0chPL8oJ0Xx/38A)
## [Charm](https://github.com/Aearnus/charm), 25 bytes
```
" Hello, World! " pstring
```
[Try it online!](https://tio.run/##S85ILMr9/19JwSM1JydfRyE8vygnRVFBSaGguKQoMy/9/38A)
## [Check](https://github.com/ScratchMan544/check-lang), 16 bytes
```
"Hello, World!"o
```
[Try it online!](https://tio.run/##S85ITc7@/1/JIzUnJ19HITy/KCdFUSn//38A)
## [Cheddar](http://cheddar.vihan.org/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##S85ITUlJLPr/v6AoM69EySM1JydfRyE8vygnRVHp/38A)
## [Chef](http://search.cpan.org/~smueller/Acme-Chef/), 236 bytes
```
H.

Ingredients.
72 l h
101 l e
108 l l
111 l o
44 l C
32 l S
87 l w
114 l r
100 l d
33 l X

Method.
Put X.Put d.Put l.Put r.Put o.Put w.Put S.Put C.Put o.Put l.Put l.Put e.Put h.Pour contents of mixing bowl into baking dish.

Serves 1.
```
[Try it online!](https://tio.run/##TY8xDoMwDEV3n8IniEhBgp2lHSohsbAWYkjUNJFCKL196mRieU/@/oO9aFpTuguAh9sCKUMu7gLaG1rUICvJJnbHtiBlnj00DauHOrdG6FrWycucBi5XbAV1zZoAnhS1VwKGI@IkMlWhLQyFvvAsHAv7S24vpEItBn8EXLyL@WD0K37Mz7gNZ39aNC56nF/vHCiza35vpPClHaVI6Q8)
## [Chez Scheme](https://cisco.github.io/ChezScheme/), 24 bytes
```
(display"Hello, World!")
```
[Try it online!](https://tio.run/##K07OSM1N1QWSVf//a6RkFhfkJFYqeaTm5OTrKITnF@WkKCpp/v8PAA)
## [CHICKEN Scheme](https://www.call-cc.org/), 22 bytes
```
(print"Hello, World!")
```
[Try it online!](https://tio.run/##K07OSM1N1U3OyEzOTs37/1@joCgzr0TJIzUnJ19HITy/KCdFUUnz/38A)
## [Chip](https://github.com/Phlarx/chip), 97 bytes
```
!ZZZZZZZZZZZZt
|))))))x)))))f
|)xx)x-))xxxa
|)))))-))x))c
)))))x-))))g
)-))))-x)xd
    b e^b^e
```
[Try it online!](https://tio.run/##S87ILPj/XzEKCZRw1WiCQQWYTANyKyo0K3SBAhUViVBJXbB0MhdEoS6ITOfSBNO6QMUpXApAkKSQGpcUl/r//3/dcgA)
## [CIL (Mono IL assembler)](http://www.mono-project.com/docs/tools+libraries/tools/monodis/), 121 bytes
```
.assembly H{}.method static void H(){.entrypoint ldstr"Hello, World!"call void[mscorlib]System.Console::Write(string)ret}
```
[Try it online!](https://tio.run/##HcsxCsMwDEDRq6iZEmh9gKxdvHfIUDo4tmgFslUsETAhZ3dD18/7kfiWpUjvLqhiXrmB3w@X0T6SQC0YRdiEEvhx2h0Wq@0rVAw4qdXBI7NcYZHK6TLEwPzXz6zxTLS@Hk0Ns7tLUWGc56WS4XiuVN5TRTt6/wE)
## [Cinnamon Gum](https://github.com/quartata/cinnamon-gum), 15 bytes
```
00000000: 2201 1d92 93bd 33f1 a12f 2a4e 940b 32    ".....3../*N..2
```
[Try it online!](https://tio.run/##LcHBDYAgDAXQVX48mlhpy6UO4Q4gYjyAJ@evmvjedvae2tWn427u4bdAJDC4mMA0F6hWRmKpkBR3WAwZKngN9FGieVyJxP0B)
## [cixl](https://github.com/basic-gongfu/cixl), 26 bytes
```
use: cx;'Hello, World!'say
```
[Try it online!](https://tio.run/##S86syPn/v7Q41UohucJa3SM1JydfRyE8vygnRVG9OLHy/38A)
## [CJam](https://sourceforge.net/p/cjam), 15 bytes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##S85KzP3/X8kjNScnX0chPL8oJ0VR6f9/AA)
## [Clean](https://clean.cs.ru.nl/), 33 bytes
```
module main
Start="Hello, World!"
```
[Try it online!](https://tio.run/##S85JTcz7/z83P6U0J1UhNzEzjyu4JLGoxFbJIzUnJ19HITy/KCdFUen//3/JaTmJ6cX/dZMA)
## [CLIPS](http://www.clipsrules.net/), 29 bytes
```
(print"Hello, World!")
(exit)
```
[Try it online!](https://tio.run/##S87JLCj@/1@joCgzr0TJIzUnJ19HITy/KCdFUUmTSyO1IrNE8/9/AA)
## [Clojure](https://clojure.org/), 22 bytes
```
(print"Hello, World!")
```
[Try it online!](https://tio.run/##S87JzyotSv3/X6OgKDOvRMkjNScnX0chPL8oJ0VRSfP/fwA)
## [COBOL (GNU)](https://sourceforge.net/projects/open-cobol/), 56 bytes
```
PROGRAM-ID.H.PROCEDURE
DIVISION.DISPLAY "Hello, World!".

```
[Try it online!](https://tio.run/##S85Pys/RTc8r/f8/IMjfPcjRV9fTRc9DD8hxdnUJDXLlcvEM8wz29PfTc/EMDvBxjFTySM3JyddRCM8vyklRVNLj@v//X3JaTmJ68X9dNwA)
## [Cobra](http://cobra-language.com/), 40 bytes
```
class H
	def main
		print'Hello, World!'
```
[Try it online!](https://tio.run/##S85PKkr8/z85J7G4WMGDizMlNU0hNzEzj4uTs6AoM69E3SM1JydfRyE8vygnRVH9/38A)
## [Coconut](http://coconut-lang.org/), 22 bytes
```
"Hello, World!"|>print
```
[Try it online!](https://tio.run/##S85Pzs8rLfn/X8kjNScnX0chPL8oJ0VRqcauoCgzDygOAA)
## [CoffeeScript 1](http://coffeescript.org/), 28 bytes
```
console.log("Hello, World!")
```
[Try it online!](https://tio.run/##S85PS0tNLU4uyiwo@f8/OT@vOD8nVS8nP11DySM1JydfRyE8vygnRVFJ8/9/AA)
## [CoffeeScript 2](http://coffeescript.org/), 28 bytes
```
console.log("Hello, World!")
```
[Try it online!](https://tio.run/##S85PS0tNLU4uyiwoMfr/Pzk/rzg/J1UvJz9dQ8kjNScnX0chPL8oJ0VRSfP/fwA)
## [Commentator](https://github.com/SatansSon/Commentator), 197 bytes
```
         {-        -}!/*{-{-           {-         -}!  /*       /*/*   /*-}-}#    {-   -}!/*{- e#-}///*{-e#-}//{-#  -}!{-# e#-}///*{-{-/*   /*{-e#-}//   /*-}-}             /*#   {-            -}!/*
```
[Try it online!](https://tio.run/##VY5BCsAwCAS/YvEmiG8qJcc0UHIT325JGpNmL46urF4l53TXs5bHHULKQWyHkPIabG6zAYRGJ9RRiI0N5@rIgIRsIg0/UsZutro85RESazMR/hLC/ZU45P4C)
## [Commercial](https://github.com/tuxcrafting/commercial), 83 bytes
```
"Hello, World!" - Satisfied Consumer of Hello
Hello has been selling out worldwide!
```
[Try it online!](https://tio.run/##FcsxDoAgDAXQ3VN8mfUULu4OzghFmwBNLMbjV9zfC1IK3YF9NnMr5SwTdrlzHB1mbL6xJqaIRao@XUISdFBcXnEQVWg/XE/I0/D@8eVIo9kH)
## [Common Lisp](http://www.clisp.org/), 22 bytes
```
(princ"Hello, World!")
```
[Try it online!](https://tio.run/##S87JLC74/1@joCgzL1nJIzUnJ19HITy/KCdFUUnz/38A)
## [Condit](https://github.com/TryItOnline/condit), 41 bytes
```
when H=""then set H="Hello, World!"put H

```
[Try it online!](https://tio.run/##S87PS8ks@f@/PCM1T8HDVkmpBMQoTi0BcTxSc3LydRTC84tyUhSVCkqBglz//wMA)
## [Convex](https://github.com/GamrCorps/Convex), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##S87PK0ut@P9fySM1JydfRyE8vygnRfH/fwA)
## [Cood](https://github.com/jesobreira/cood/tree/php-interpreter), 381 bytes
```
More 72 of this
Im very hungry
More 29 of this
Im very hungry
More 7 of this
Im very hungry
Im very hungry
More 3 of this
Im very hungry
Less 67 of this
Im very hungry
Less 12 of this
Im very hungry
More 55 of this
Im very hungry
More 24 of this
Im very hungry
More 3 of this
Im very hungry
Less 6 of this
Im very hungry
Less 8 of this
Im very hungry
Less 67 of this
Im very hungry
```
[Try it online!](https://tio.run/##S87PT/n/3ze/KFXB3EghP02hJCOzmMszV6EstahSIaM0L72okgssbWSJV9oclyw2xca4FPukFhcrmJnjlTbE705TU/zeMMErTcBleGUtyPPV//8A)
## [Corea](https://github.com/ConorOBrien-Foxx/Corea), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##S84vSk38/98jNScnX0chPL8oJ0Xx/38A)
## [COW](https://bigzaphod.github.io/COW/), 261 bytes
```
MOoMOoMOomoOMOomoOMOomoOmoOMoOmoOMoOmoOmoOMoOMOOMoOMoOMoOMoOMOOmoOMoOMoOMoOMOOmoOMoOMoOMoOMoOmoOMOoMOomoOMoOMoOMoOmOomOomOoMOomoomOoMOomoomOoMoOMoOMoOmoomoOmoOmoOMoomoOMOoMOomoOMOoMoomoOMooMooMoOmoOMoOMoOMoOMoOmoOMoOMoOMoOMooMoOmoOMOoMOomoOMOOmoOMOoMoomOomOomoo
```
[Try it online!](https://tio.run/##bU5BDsAgDHqh4RE7G457fqewtbqYEEKJIBfviAYanVh5ioUtGsQJfP7xdCrL0xynIH8XFXw3KMitZz5zIYXTpwX@ZwBV4iVkxAM)
## [cQuents 0](https://github.com/stestoltz/cQuents), 15 bytes
```
Hello, World!?0
```
[Try it online!](https://tio.run/##Sy4sTc0rKf7/3yM1JydfRyE8vygnRdHe4P9/AA)
## [Crayon](https://github.com/ETHproductions/crayon), 16 bytes
```
"Hello, World!"q
```
[Try it online!](https://tio.run/##Sy5KrMzP@/9fySM1JydfRyE8vygnRVGp8P9/AA)
## [Crystal](https://crystal-lang.org), 20 bytes
```
puts "Hello, World!"
```
[Try it online!](https://tio.run/##Sy6qLC5JzPn/v6C0pFhBySM1JydfRyE8vygnRVHp/38A)
## [CSL](https://github.com/jammy-dodgers/CSL), 81 bytes
```
p*++1+p*DD+p---p+++pDDp-*+++Dpp&&D&D++1D&D&DD-~pD+++ppDD&--~pD+*D+p*-DDDDD*D++1E!
```
[Try it online!](https://tio.run/##HcuxDcBACAPAWdJQYLnIDv5J0n5h6fusTiA0lq3jObvKCdxwSjBJA7Bk9gzZEQq10KT4WgNaBP@S/ZbUXI5bV9UH)
## [Cubically](https://github.com/aaronryank/cubically), 78 bytes
```
RU+432@6+50-4@6+3-4@6@6+1-00@6-331@6-00@6+4110@6+0000@6+1-00@6-0@6-2+4@6-331@6
```
[Try it online!](https://tio.run/##Sy5NykxOzMmp/P8/KFTbxNjIwUzb1EDXBEgZg0ggbahrYOBgpmtsbAgkQUxtE0NDEGVgAOZB5UHYSNsEpvL/fwA)
## [Cubix](https://github.com/ETHproductions/cubix), 29 bytes
```
./v.o;@?/"!dlroW"S',u/"Hello"
```
[Try it online!](https://tio.run/##Sy5Nyqz4/19Pv0wv39rBXl9JMSWnKD9cKVhdp1RfySM1Jydf6f9/AA)
## [Curry (Sloth)](http://babel.ls.fi.upm.es/research/Sloth/), 37 bytes
```
import IO
main=putStr"Hello, World!"

```
[Try it online!](https://tio.run/##Sy4tKqrULc7JL8n4/z8ztyC/qETB058rNzEzz7agtCS4pEjJIzUnJ19HITy/KCdFUYnr/38A)
## [Cy](https://github.com/cyoce/Cy), 18 bytes
```
"Hello, World!" :<
```
[Try it online!](https://tio.run/##S678/1/JIzUnJ19HITy/KCdFUUnByub/fwA)
## [D](https://dlang.org/), 52 bytes
```
import std.stdio;void main(){"Hello, World!".write;}
```
[Try it online!](https://tio.run/##S/n/PzO3IL@oRKG4JEUPiDPzrcvyM1MUchMz8zQ0q5U8UnNy8nUUwvOLclIUlfTKizJLUq1r//8HAA)
## [D2](https://github.com/ConorOBrien-Foxx/Attache/blob/master/D2.md), 22 bytes
```
"r8$.s$o;Hello, World!
```
[Try it online!](https://tio.run/##SzH6/1@pyEJFr1gl39ojNScnX0chPL8oJ0Xx/38A)
## [Dash](https://wiki.debian.org/Shell), 18 bytes
```
echo Hello, World!
```
[Try it online!](https://tio.run/##S0kszvj/PzU5I1/BIzUnJ19HITy/KCdF8f9/AA)
## [dc](https://www.gnu.org/software/bc/manual/dc-1.05/html_mono/dc.html), 16 bytes
```
[Hello, World!]P
```
[Try it online!](https://tio.run/##S0n@/z/aIzUnJ19HITy/KCdFMTbg/38A)
## [Deadfish~](https://github.com/TryItOnline/deadfish-), 1 byte
```
w
```
[Try it online!](https://tio.run/##S0lNTEnLLM7Q/f@//P9/AA)
## [Decimal](https://github.com/aaronryank/Decimal), 45 bytes
```
13072101108108111044032087111114108100033D301
```
[Try it online!](https://tio.run/##S0lNzsxNzPn/39DYwNzI0MDQ0MAChIC0iYmBsZGBhbkhCJiAxQ0MjI1djA0M//8HAA)
## [Del|m|t](https://github.com/MistahFiggins/Delimit), 30 bytes
```
=#:#Hello, World!#/##3#=#?#9#"
```
[Try it online!](https://tio.run/##S0nNyczNLPn/31bZStkjNScnX0chPL8oJ0VRWV9Z2VjZVtle2VJZ6f///8oA)
## [Deorst](https://github.com/SatansSon/Deorst), 15 bytes
```
'Hello, World!'
```
[Try it online!](https://tio.run/##S0nNLyou@f9f3SM1JydfRyE8vygnRVH9/38A "Deorst – Try It Online")
## [Detour](https://github.com/cyoce/detour), 19 bytes
```
`u
@"Hello, World!"
```
[Try it online!](https://tio.run/##S0ktyS8t@v8/oZTLQckjNScnX0chPL8oJ0VR6f9/AA)
## [Dirty](https://github.com/Ourous/dirty), 16 bytes
```
'Hello, World!'‼
```
[Try it online!](https://tio.run/##S8ksKqn8/1/dIzUnJ19HITy/KCdFUf1Rw57//wE)
## [DOBELA](https://deewiant.iki.fi/projects/dobelx64/), 123 bytes
```
+ +..,.,..,,.,.,.,.,$,,.,..,,,..,,..,,$,,.,,,..,,...,..,$,.,,,.,.,.,...,,.$,.,.....,,,.,.,.,$.,,..,.,.,,..,,,,$
 ^




++.#
```
[Try it online!](https://tio.run/##S8lPSs1J/P9fW0FbT08HCPV0dPSgUEUHKgARBWKwCIwLllOBCEAgWFwFwtJDiKtAdIMgxDgdFS6FOC4Q0NbWU/7/HwA)
## [Dodos](https://github.com/DennisMitchell/dodos), 159 bytes
```
	* 2
	1 0 4
	L
	L
	1 *
	4 3 1
	2 1 1
	2 2 3
	1 *
	4 *
	L
	+ 0 0 4
	3 1 1
L
	3 1 4
*
	2 4
+
	dot
i
	+ j
j
	
	dip + dab
0
	
	
	
	
	
1
	i + 0
2
	i 1
3
	i 2
4
	i 3
```
[Try it online!](https://tio.run/##PYxBDsMwCATP7Cs426pkY17Qcz7RyhfnEEdK3h9qnCoCaReYpfbaDzMKLKDMiRW0zM4cQMqFM0g43yJcnkuYWByZmSqTWW6jCI4rIqj2E83BFStozG3nyPXzRfLxX@N9G@sEcZNRXATqUsyuvp@tb4e93j8)
## [Dreaderef](https://github.com/ScratchMan544/Dreaderef), 31 bytes
```
"Hello, World!\n"
```
[Try it online!](https://tio.run/##SylKTUxJLUpN@/9fic2DLZUtBwjz2XTYFNjCgXQRkJfCpsgWk6f0/z8A)
## [DStack](https://github.com/alejandrocoria/DStack), 21 bytes
```
@0
Hello, World!
@
ad
```
[Try it online!](https://tio.run/##SykuSUzO/v/fwYDLIzUnJ19HITy/KCdFkcuBKzHl/38A)
## [eacal](https://github.com/ConorOBrien-Foxx/eacal), 24 bytes
```
put string Hello, World!
```
[Try it online!](https://tio.run/##S01MTsz5/7@gtEShuKQoMy9dwSM1JydfRyE8vygnRfH/fwA)
## [ecpp + C (gcc)](https://github.com/aaronryank/ecpp), 30 bytes
```
main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##S00uKNBN/v8/NzEzT0OzuqC0pFhDySM1JydfRyE8vygnRVFJ07r2//9/yWk5ienF/3XD8/J1E3NyAA)
## [ecpp + C++ (gcc)](https://github.com/aaronryank/ecpp), 51 bytes
```
#include<cstdio>
int main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##S00uKNAF4v//lTPzknNKU1JtkotLUjLz7bgy80oUchMz8zQ0qwtKS4o1lDxSc3LydRTC84tyUhSVNK1r//8HAA)
## [Egel](https://github.com/egel-lang/egel), 52 bytes
```
import"io.ego"using IO
def main=print"Hello, World!"
```
[Try it online!](https://tio.run/##S01Pzfn/PzO3IL@oRCkzXy81PV@ptDgzL13B058rJTVNITcxM8@2oCgzr0TJIzUnJ19HITy/KCdFUen/fwA)
## [Element](https://github.com/PhiNotPi/Element), 17 bytes
```
Hello\,\ World\!`
```
[Try it online!](https://tio.run/##S81JzU3NK/n/3yM1Jyc/RidGITy/KCclRjHh/38A)
## [ELF (x86/x64, Linux)](https://refspecs.linuxfoundation.org/elf/elf.pdf), 59 bytes
```
0000000: 7f 45 4c 46 01 00 00 00 00 00 00 00 00 90 43 0d  .ELF..........C.
0000010: 02 00 03 00 19 90 43 0d 19 90 43 0d 04 00 00 00  ......C...C.....
0000020: b9 2e 90 43 0d b2 0d cd 80 cc 20 00 01 00 48 65  ...C...... ...He
0000030: 6c 6c 6f 2c 20 57 6f 72 6c 64 21                 llo, World!
```
[Try it online!](https://tio.run/##bc49CwIxDAbg3V/xuktJc@l9uIri4O5@vXYqHPj/obapeiKGNITS96EhxZyp1RFDhDiIh/QgC6L/PRGkAy2AOd8u5lMns1PIFopYH3d12mmLfO8km4k30Y55UVyoeQKHLTVznX7BSPAe3AT9rYzonVLNMHW9hkZ1heq9dgRr0A11H1gvBWzxWymtB9zXR1r2OT8B)
## [Elixir](https://elixir-lang.org/), 22 bytes
```
IO.puts"Hello, World!"
```
[Try it online!](https://tio.run/##S83JrMgs@v/f01@voLSkWMkjNScnX0chPL8oJ0VR6f9/AA)
## [ELVM-IR, 66 bytes](https://github.com/shinh/elvm), 66 bytes
```
load B,A
putc B
add A,1jne 0,A,13exit
.data
.string"Hello, World!"
```
[Try it online!](https://tio.run/##S80py9XNLPr/Pyc/MUXBSceRq6C0JFnBiSsxJUXBUccwKy9VwUAHyDBOrcgs4dJLSSxJ5NIrLinKzEtX8kjNycnXUQjPL8pJUVT6/x8A)
## [Emacs Lisp](https://www.gnu.org/software/emacs/manual/eintr.html), 22 bytes
```
(princ"Hello, World!")
```
[Try it online!](https://tio.run/##S81NTC7WzcksLvj/X6OgKDMvWckjNScnX0chPL8oJ0VRSfP/fwA)
## [Emmental](https://github.com/catseye/Emmental), 57 bytes
```
#33#100#108#114#111#87#32#44#111#108:#101#72.............
```
[Try it online!](https://tio.run/##S83NTc0rScz5/1/Z2FjZ0MAAiC2UDQ1NgNhQ2cJc2dhI2QTCAUpYAQlDZXMjPWTw/z8A)
## [Emoji](https://esolangs.org/wiki/Emoji), 24 bytes
```
💬Hello, World!💬➡
```
[Try it online!](https://tio.run/##S83Nz8r8///D/ElrPFJzcvJ1FMLzi3JSFEECj@Yt/P8fAA)
## [Emojicode](http://www.emojicode.org/), 37 bytes
```
🏁🍇😀🔤Hello, World!🔤🍉
```
[Try it online!](https://tio.run/##S83Nz8pMzk9J/f//w/z@xg/ze9s/zJ/R8GH@lCUeqTk5@ToK4flFOSmKIAGgZOf//wA)
## [Emotinomicon](https://github.com/ConorOBrien-Foxx/Emotinomicon), 30 bytes
```
😭!dlroW ,olleH😲⏪⏬⏩
```
[Try it online!](https://tio.run/##S83NL8nMy8/NTM7P@///w/wZaxVTcorywxV08nNyUj2AApse9a961L/mUf/K//8B)
## [Enlist](https://github.com/alexander-liao/enlist), 15 bytes
```
“Hello, World!”
```
[Try it online!](https://tio.run/##S83LySwu@f//UcMcj9ScnHwdhfD8opwUxUcNc///BwA)
## [Erlang (escript)](http://erlang.org/doc/man/escript.html), 37 bytes
```

main(_)->io:fwrite("Hello, World!").
```
[Try it online!](https://tio.run/##Sy3KScxL100tTi7KLCj5/58rNzEzTyNeU9cuM98qrbwosyRVQ8kjNScnX0chPL8oJ0VRSVPv/38A)
## [ETA](http://www.miketaylor.org.uk/tech/eta/doc/), 73 bytes
```
ninenahaenatoenaaaenatsentnoeniiensaenatsenatoenehnahoentoaeooooooooooooo
```
[Try it online!](https://tio.run/##TYo7CgAwDELP6iAkixma@6cSKNTh@UE2ZpSiEDC6DGw6VMs1kzpv2QPDb3sXWL9mLg)
## [evil](https://web.archive.org/web/20070103000858/www1.pacific.edu/~twrensch/evil/index.html), 70 bytes
```
aeeeaeeewueuueweeueeuewwaaaweaaewaeaawueweeeaeeewaaawueeueweeaweeeueuw
```
[Try it online!](https://tio.run/##JYs5CsBADAPfOsUUgbSOnu9dOyAJdPk9bzfqMGWV0RokQATD1Wzz71jrJkx6j@k@)
## [Explode](https://github.com/stestoltz/Explode), 68 bytes
```
@1+E
@1+17
@1+1e
@1+1e
@1+1h
@1+c

@1+T
@1+1h
@1+1k
@1+1e
@1+16
@1+1
```
[Try it online!](https://tio.run/##S60oyMlPSf3/38FQ25ULSBiag8lUJDIDRCZzgcgQhIBhNpISMzD5/z8A)
## [ExtraC](https://github.com/ConorOBrien-Foxx/extrac), 37 bytes
```
printf(quote(Hello\x2c\x20World\x21))
```
[Try it online!](https://tio.run/##S60oKUpM/v@/oCgzryRNo7A0vyRVwyM1Jyc/psIoGYgNwvOLclKADENNzf//AQ)
## [F# (.NET Core)](https://www.microsoft.com/net/core/platform), 21 bytes
```
printf"Hello, World!"
```
[Try it online!](https://tio.run/##SyvWTc4vSv3/v6AoM68kTckjNScnX0chPL8oJ0VR6f9/AA)
## [F# (Mono)](http://www.mono-project.com/), 21 bytes
```
printf"Hello, World!"
```
[Try it online!](https://tio.run/##SyvWzc3Py///v6AoM68kTckjNScnX0chPL8oJ0VR6f9/AA)
## [Face](https://github.com/KeyboardFire/face), 41 bytes
```
(Hello, World!
)\$*m%*7%+%%%,c'$,ioow%$%o
```
[Try it online!](https://tio.run/##S0tMTv3/X8MjNScnX0chPL8oJ0WRSzNGRStXVctcVVtVVVUnWV1FJzM/v1xVRTX//38A)
## [Factor](https://factorcode.org/), 28 bytes
```
USE: io "Hello, World!"print
```
[Try it online!](https://tio.run/##S0tMLskv@v8/NNjVSiEzX0HJIzUnJ19HITy/KCdFUamgKDOv5P9/AA)
## [Fantom](http://fantom.org/), 43 bytes
```
class H{Void main(){echo("Hello, World!")}}
```
[Try it online!](https://tio.run/##S0vMK8nP/f8/OSexuFjBozosPzNFITcxM09Dszo1OSNfQ8kjNScnX0chPL8oJ0VRSbO29v9/AA)
## [Felix](https://github.com/felix-lang/felix), 21 bytes
```
print"Hello, World!";
```
[Try it online!](https://tio.run/##S0vNyaz4/7@gKDOvRMkjNScnX0chPL8oJ0VRyfr/fwA)
## [FerNANDo](https://esolangs.org/wiki/FerNANDo), 109 bytes
```
7 7
3
5 5
6 5
4 3 3
0 5 3 0 7 3 0 0
0 5 7 0 0 5 0 4
0 6 5 2 4 6 2 3
0 6 6 0 7 7 2 3
0 6 6 2 5 4 7 4
2 2
3 5
3
```
[Try it online!](https://tio.run/##TYzBCcBACAT/VrEliHpnPYEkzwukfzB7voLouDJ4X@861vlUJVJcBoZMdsDhohikIntq59wbqQhmujAEae1P1vbzl41O8BJiMHF@96oP)
## [FEU](https://github.com/tuxcrafting/feu), 15 bytes
```
a/Hello, World!
```
[Try it online!](https://tio.run/##S0st/f8/Ud8jNScnX0chPL8oJ0Xx/38A)
## [Fireball](https://github.com/okx-code/Fireball), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##S8ssSk1KzMn5/1/JIzUnJ19HITy/KCdF8f9/AA)
## [fish](https://fishshell.com/), 18 bytes
```
echo Hello, World!
```
[Try it online!](https://tio.run/##S8ssztAtzkjNyfn/PzU5I1/BA8jM11EIzy/KSVH8/x8A)
## [Fission](https://github.com/C0deH4cker/Fission), 17 bytes
```
R"Hello, World!";
```
[Try it online!](https://tio.run/##S8ssLs7Mz/v/P0jJIzUnJ19HITy/KCdFUcn6/38A)
## [Fission 2](https://github.com/C0deH4cker/Fission), 17 bytes
```
R"Hello, World!";
```
[Try it online!](https://tio.run/##S8ssLs7MzzP6/z9IySM1JydfRyE8vygnRVHJ@v9/AA)
## [Flipbit](https://github.com/cairdcoinheringaahing/Flipbit), 148 bytes
```
>^>>>^>>>.^<<^<^<<^>>>>>.^<<<^>>>..^<^>.^<^<<<<<^>>>>>>.<<^<^>>>.^<^<^<<^<^<^>>>>>>.<<<^<^<^>>>>>.^<<^<^<^>>>>.<^<^<^<^>>>>.<<<^>>>.^<<^<<<<^>>>>>>.
```
[Try it online!](https://tio.run/##S8vJLEjKLPn/3y7Ozg6M9eJsbOJsQISdHZQLZuoBWXEgLkgAJmunB1YMUQfRBeVD5JC4esiSehAmjGNjg7AZyez//wE)
## [FOCAL-69](http://www.cozx.com/dpitts/), 20 bytes
```
1.1t "Hello, World!"
```
[Try it online!](https://tio.run/##S8tPTsz5/99Qz7BEQckjNScnX0chPL8oJ0VR6f9/AA)
## [Foo](https://esolangs.org/wiki/Foo), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##S8vP//9fySM1JydfRyE8vygnRfH/fwA)
## [Forked](https://github.com/aaronryank/Forked), 42 bytes
```
89*@AA*i@7+@@3+@4B*@C'!sF+!@3+@6'@8'!3B*!&
```
[Try it online!](https://tio.run/##S8svyk5N@f/fwlLLwdFRK9PBXNvBwVjbwcRJy8FZXbHYTVsRxDVTd7BQVzR20lJU@/8fAA)
## [Forte](https://github.com/judofyr/forter), 25 bytes
```
1PRINT"Hello, World!":END
```
[Try it online!](https://tio.run/##S8svKkn9/98wIMjTL0TJIzUnJ19HITy/KCdFUcnK1c/l/38A)
## [Forth (gforth)](http://www.complang.tuwien.ac.at/forth/gforth/Docs-html/), 17 bytes
```
.( Hello, World!)
```
[Try it online!](https://tio.run/##S8svKsnQTU8DUf//62koeKTm5OTrKITnF@WkKGr@/w8A)
## [Fortran (GFortran)](https://gcc.gnu.org/fortran/), 28 bytes
```
print'("Hello, World!")'
end
```
[Try it online!](https://tio.run/##S8svKilKzNNNT4Mw/v8vKMrMK1HXUPJIzcnJ11EIzy/KSVFU0lTnSs1L@f8fAA)
## [Fourier](https://github.com/beta-decay/Fourier), 15 bytes
```
`Hello, World!`
```
[Try it online!](https://tio.run/##S8svLcpMLfr/P8EjNScnX0chPL8oJ0Ux4f9/AA)
## [FRACTRAN](https://github.com/DennisMitchell/ffi), 86 bytes
```
(3^72*5^101*7^108*11^108*13^111*17^44*19^32*23^87*29^111*31^114*37^108*41^100*43^33)/2
```
[Try it online!](https://tio.run/##JYtBCoNAEAS/Yxok9vTI6mcGJBDworL6fidGL9WH6vrW6XPUaclsFMXQBzuiXBxAPqMgCZZwB8eQwRRDgY230HWjQ0/k/6iDK6TX2zLPdTvmddmzrT8)
## [Fueue](https://github.com/TryItOnline/fueue), 40 bytes
```
72:108)<101[44+-6:114)32[100 33H]87]:111
```
[Try it online!](https://tio.run/##SytNLU39/9/cyMrQwELTxtDAMNrERFvXzMrQ0ETT2Cja0MBAwdjYI9bCPBYoZPj/PwA)
## [Funciton](https://github.com/Timwi/Funciton), 209 bytes
```
╔══════════╗
║2388215291╟
║3945970717║
║0943959830║
║0709090713║
║3592077341║
║6068961777║
║8210571695║
║52834632  ║
╚══════════╝
```
[Try it online!](https://tio.run/##hc5NCgIxDAXgvaeYI@SnSfrOIwhuxo1zjxEsgiDerRepHexslWTzvkVeTst8PF8vc2u13GtZf@7jUMtNNGdhE3At7w0UyRAUHD1sQEgKQ1baIQh9gnWAGoQiNPEAJ89wjthv9AqyYIcNMMmaXGWavvD89@yrtQ8)
## [Functoid](https://github.com/bforte/Functoid), 53 bytes
```
"H","e","l","l","o",","," ","W","o","r","l","d","!",@
```
[Try it online!](https://tio.run/##SyvNSy7Jz0z5/1/JQ0lHKRWIc6A4H4hBUAGIw6H8IqhcChArKuk4/P//L7@gJDM/r/i/biEA)
## [Funky](https://github.com/TehFlaminTaco/Funky), 20 bytes
```
write"Hello, World!"
```
[Try it online!](https://tio.run/##SyvNy678/7@8KLMkVckjNScnX0chPL8oJ0VR6f9/AA)
## [Gaia](https://github.com/splcurran/Gaia), 14 bytes
```
“Hello, World!
```
[Try it online!](https://tio.run/##S0/MTPz//1HDHI/UnJx8HYXw/KKcFMX//wE)
## [Gambit Scheme (gsi)](http://gambitscheme.org), 22 bytes
```
(print"Hello, World!")
```
[Try it online!](https://tio.run/##K07OSM1N1U1PzE3KLPn/X6OgKDOvRMkjNScnX0chPL8oJ0VRSfP/fwA)
## [Gaot++](https://github.com/tuxcrafting/gaot-plus-plus), 679 bytes
```
baaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa bleeeeeeeeeeeeet bleet bleeeeeeeeeeeeet bleeeeeeeeeeeeet bleeeeeeeeeet
baaaaaaaaaaaaaaaaaaaaaaaaaaaaaa bleet bleeeeeeeeeeeeet bleeeeeeeeeet
baaaaaaaa bleet bleeeeeeeeeeeeet bleeeeeeeeeet
bleeeeeeeeeeeeet bleeeeeeeeeet
bleeeeeeeeeeeeet baaaa bleet bleeeeeeeeeet
baaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa bleeeeeeeeeeeeet baaaaaaaaaaaaa bleet bleeeeeeeeeet
bleeeeeeeeeet
bleeeeeeeeeeeeeeet baaaaaaaaaaaaaaaa bleet bleeeeeeeeeeeeet bleeeeeeeeeet bleeeeeeeeeeeeeeet
bleeeeeeeeeeeeet baaaa bleet bleeeeeeeeeeeeet bleeeeeeeeeet
baaaa bleet bleeeeeeeeeet
bleeeeeeeeeet
baaaaaaaaaaaaaa bleet bleeeeeeeeeet
baaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa bleeeeeeeeeet
```
[Try it online!](https://tio.run/##S0/MLyko@P8/KZEYoJCUk4oMSsACJdiFcQqUcCURYQ3xhhCpnFRpHEYTdD32cCLkQVQXYLgH0wxiPa6AaRLxnsUV7MR4IJEIL5OY5Er@/wcA)
## [GAP](https://www.gap-system.org/), 23 bytes
```
Print("Hello, World!");
```
[Try it online!](https://tio.run/##S08s@P8/oCgzr0RDySM1JydfRyE8vygnRVFJ0/r/fwA)
## [Glypho](https://web.archive.org/web/20060621185740/http://www4.ncsu.edu/~bcthomp2/glypho.txt), 456 bytes
```
aabcaabcabbaaabcabbaabababbcababababababababababaabcabcaabbaabbcabbbaabcabbaabababbcaabcabbaabababbbaabbaabcabcaabbaaabcabcaabbaabbaabababababbbabbbaabcabbaaabcabbaaabcabbaabababbbaabbaabcabcaabbaabababababbaabababbaababaabcaabcabbaaabcabbaabababbaabababbaabbaabbbabbbababaabcabbaaabcabbaaabcabbaabbcaabcabcaabbaabbbabababababbbaabcabbaaabcabbaaabcabbaabbbaabcabcaabbaaabcabcaabbaaabcabcaabbaabbbaabcabbaabababababbcabbbaabcabbaaabcaabcabbaaabcabbaabbcabbb
```
[Try it online!](https://tio.run/##fVFBDoAwCHsr3UEPJnr19ShkE9jAEFKWtKVk23Ff@8lMhKYN0IeQkjkp5YhERuVj0cU3Otl00YPMHQh@ea7Vz/QUsL7NoXbfTT@7h1dzGpe71tW3z34h4/iDyTvL9XKYHw)
## [Glypho (shorthand)](https://web.archive.org/web/20060621185740/http://www4.ncsu.edu/~bcthomp2/glypho.txt), 114 bytes
```
11+1+d*ddddd1-+*o1+d*1+do\1-+1-++ddoo1+1+1+do\1-+dd+d+d11+1+d+d++ood1+1+1+*1-+oddo1+1+1+o1-+1-+1-+o1+dd*o1+11+1+*o
```
[Try it online!](https://tio.run/##NUw7DoBQCLsPxIH7uJg08Q3GGnXx9FgkUhj6Y92eY3C6Bs97LDsyIzwchpqY3FhMx1lM6wBZmV8DXOia4CTaNplUuhm7XpqCqL9fx5j5Ag)
## [gnuplot](http://www.gnuplot.info/), 31 bytes
```
set print'-
print'Hello, World!
```
[Try it online!](https://tio.run/##S88rLcjJL/n/vzi1RKGgKDOvRF2XC0J7pObk5OsohOcX5aQo/v8PAA)
## [Go](https://golang.org/), 61 bytes
```
package main
import."fmt"
func main(){Print("Hello, World!")}
```
[Try it online!](https://tio.run/##S8///78gMTk7MT1VITcxM48rM7cgv6hETyktt0SJK600LxksrKFZHVCUmVeioeSRmpOTr6MQnl@Uk6KopFn7/z8A)
## [Gol><>](https://github.com/Sp3000/Golfish), 16 bytes
```
"!dlroW ,olleH"H
```
[Try it online!](https://tio.run/##S8/PScsszvj/X0kxJacoP1xBJz8nJ9VDyeP/fwA)
## [GolfScript](http://www.golfscript.com/golfscript/), 15 btyes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##S8/PSStOLsosKPn/X8kjNScnX0chPL8oJ0VR6f9/AA)
## [Grass](https://github.com/TryItOnline/grass), 448 bytes
```
wWWWwWWWWwWWWWWwvwwWWwWWWwvWwWwwwwwWWWwWWWwWWWWWwvwWWwwwwwwwwwwwWWWwWWWWWwWWWWwvwWWwwwwwWWWWWWWWWWWWwWWWwvWwwwwwwwwwwwWWwwwwwwWWWWWWWWwWWWWWWWwwWWWWWWwwwwwwwvwWWWWWWWwwwwwwwwwWWWWWWWWWWWWWwWWWwvWwwwwwwwwwwwwwwwwwWWwwwwwwwwwwwwWWWWWWWWWWWWWWWWWwvwWwWwwwwwwwwWwwwwwwWwwwwwwWwwwwwwwWwwwwwwwWwwwwwwwwwwwwwwWWWWWWWWWWWWWWWWWWwvwwWWWWWWWWWWWWWWWWWWWWWWwWWWwwwvWWwWWWWWWWWWWWWWWWWWWWWWwwwwWWwwwwwwwwwWwwwwwwWwwwWwwwwwwwwwWWWWWWWWWWWWwWwwwwwwwwwwwwwwwwwwvw
```
[Try it online!](https://tio.run/##dVBBDsAgCHtmzzvtPhP6fKZBFCYjUQgttXg/V2uqBDCOXaCQVlN64ogJLgKszQi6yEIRwuXiFBPLC@9Mmuw@ecgWulm9GHGTXBRU6ch/WvPDqqD5lr3dB89Og4F6XZ6L9sdVXw)
## [Grime](https://github.com/iatorm/grime), 2 bytes
```
.+
```
[Try it online!](https://tio.run/##Sy/KzE39/19P@/9/j9ScnHwdhfD8opwURQA)
## [Groovy](http://groovy-lang.org/), 20 bytes
```
print'Hello, World!'
```
[Try it online!](https://tio.run/##Sy/Kzy@r/P@/oCgzr0TdIzUnJ19HITy/KCdFUf3/fwA)
## [GS2](https://github.com/nooodl/gs2), 2 bytes
```
↕h
```
[Try it online!](https://tio.run/##Sy82@v//UdvUjP//AQ)
## [Guile](https://www.gnu.org/software/guile/), 24 bytes
```
(display"Hello, World!")
```
[Try it online!](https://tio.run/##K07OSM1N1U0vzcxJ/f9fIyWzuCAnsVLJIzUnJ19HITy/KCdFUUnz/38A)
## [Half-Broken Car in Heavy Traffic](https://git.metanohi.name/hbcht.git/) (3201 bytes)
```
@outtext
     v                           >v      ^
> v  <                            v    >>^<
  v  ^  v                         v    ^
     ^  <                         v    ^
        ^                         v    ^
  >   />^<v                       v    ^
  ^  >v<  <                       v    ^
          ^                       v    ^
  ^   > />^<v                     v    ^   #
  ^   ^>v<  <                     v    ^   ^
  ^         ^                     v    ^   ^
  ^     > />^<v                   v    ^   ^
  ^     ^>v<  <                   v    ^   ^
  ^           ^                   v    ^   ^
  ^       > />^<v                 v    ^   ^
  ^       ^>v<  <                 v    ^   ^
  ^             ^                 v    ^   ^
  ^         > />^<v               v    ^   ^
  ^         ^>v<  <           >v  v    ^ >>^<
  ^               ^           ^v  v    ^ ^
  ^           > />^<v         ^v  v    ^ ^
  ^           ^>v<  <         ^v  v  >>^<^
  ^                 ^         ^v  v  ^   ^
  ^             > />^<v       ^v  v  ^   ^
  ^             ^>v<  <       ^v  v  ^   ^
  ^                   ^       ^v  v  ^   ^
  ^               > />^<v     ^v  v  ^   ^
  ^               ^>v<  <     ^v  v  ^   ^
  ^                     ^     ^v  v  ^   ^
  ^                 > />^<v   ^v  v  ^   ^
  ^                 ^>v<  <   ^v  v  ^   ^
  ^                       ^   ^v  v  ^   ^
  ^                   > />^<v ^v  v  ^   ^
  ^                   ^>v<  < ^v  v  ^   ^
  ^                         ^ ^v  v  ^   ^
  ^                     > />^<^v  v  ^   ^
  ^                >>   ^     ^ < v  ^   ^
  ^          >v<<<<<<<<<<<<    v  v  ^   ^
  ^           v   >^<          v  v>>^<  ^
  ^           v  > >v          v  v^     ^
> ^   v       v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v      ^
^ ^           v  ^^            v  v    >>^<
^ ^           v  ^^ <          v  v    ^
^ ^           v>>^<            v  v    ^
^ ^                            v  v    ^
^ ^           v^               v  v    ^
^ ^           v^               v  v    ^
^ ^           v^               v  v      v
^ ^           v^               v  v >v   <
^ ^           v^               v  v  >>^<^
^ ^        >v <^               v  v  ^   ^
^ ^         >>^^<              v  v      ^
^ ^         ^                  v  v      ^
^ ^                            v  >v     ^
^ ^                            v  ^v     ^
^ ^                            v   v     ^
^ ^                            v   v     ^
^ ^    v                       v   v     ^
^ ^    <                       v   v     ^
^     >^<                      v   v     ^
^     ^                        v   v     ^
^     v                        > ^<      ^
^     <                        ^
    >>^<
 >  ^<v
 ^ >v<<
  v
>v<
  ^
 >^<
 o>v
 v >  ^<
 v ^
```
[Try it online!](https://tio.run/##7ZZBbsQgDADvvAKpD9gPIKsv8WGrSnvbS4r296kNhACxweqhUqXmkihM7IkFmMf947Ht@/vza9s@X5vzfEWvX1AG0QFzYYLmOAAYXHrGWeSYg@bYs7gtmNkVCHS/kUVcgci/F/TkQ2o9eRuR0uvJ4xHlrcA4EajwEXkmIcC6iADrIoqGLCLCmogIayKqhiSiwLKIVueLCK@FApdZPmbuynPSo/LoMUFHi4JyfnTSr@OIyjXrFaZorzBFe4UF2ios0FbBIFAn9Qo9FZboqWASKONr9FCw1LUoGAXSdLKgWWGFApx1JQkZJcPmKqtLicplp7zdiwjpjYBCbUUHirUxYdPEOBkOy7v2MByj/qN/H017scSGK3sJCt0M1EGpxcgR8ddAupnQtHCCLWpuLA1KHwcZxYsrfYxBc@1R1CtqK37ZDSwo2lH/czTa0WBC/bg/zlH05qjqsZy20uA7VD2Y53NxPgdRZ6AW5vhcRPs/n/4dPbgEJeAJNBozxw@4798)
## [Haskell](https://www.haskell.org/), 26 bytes
```
main=putStr"Hello, World!"
```
[Try it online!](https://tio.run/##y0gszk7Nyfn/PzcxM8@2oLQkuKRIyQMokq@jEJ5flJOiqPT//7/ktJzE9OL/umUGAA)
## [Haxe](https://haxe.org/), 61 bytes
```
class Main{static function main()Sys.print("Hello, World!");}
```
[Try it online!](https://tio.run/##y0isSP3/PzknsbhYwTcxM6@6uCSxJDNZIa00L7kkMz9PIRcoqKEZXFmsV1CUmVeioeSRmpOTr6MQnl@Uk6KopGld@/8/AA)
## [Haystack](https://github.com/kade-robertson/haystack), 17 bytes
```
"Hello, World!"o|
```
[Try it online!](https://tio.run/##y0isLC5JTM7@/1/JIzUnJ19HITy/KCdFUSm/5v9/AA)
## [Hexadecimal Stacking Pseudo-Assembly Language](https://github.com/ConorOBrien-Foxx/Hexadecimal-Stacking-Pseudo-Assembly-Language), 162 bytes
```
20002140000020006440000020006C40000020007240000020006F40000020005740000020002040000020002C40000020006F40000020006C40000020006C400000200065400000200048400000140000
```
[Try it online!](https://tio.run/##yyguSMz5/9/IwMDAyNDEAARAbDMTJLYzgm1uhCTuhmCbmiPYRgZIbGfs6pHNRGGbItgmFhA2xFn//wMA)
## [Hexagony](https://github.com/m-ender/hexagony), 29 bytes
```
H;_e;r;2l.;P.QW;l/P1;@;0d;\o;
```
[Try it online!](https://tio.run/##y0itSEzPz6v8/9/DOj7VusjaKEfPOkAvMNw6Rz/A0NrB2iDFOibf@v9/AA)
## [Hodor](https://github.com/hummingbirdtech/hodor), 28 bytes
```
hodor.hod("Hello,","World!")
```
[Try it online!](https://tio.run/##y8hPyS/6/z8DROkBSQ0lj9ScnHwdJR2l8PyinBRFJc3//wE)
## [Huginn](https://codestation.org/?h-action=menu-project&menu=submenu-project&page=&project=huginn), 31 bytes
```
main(){print("Hello, World!");}
```
[Try it online!](https://tio.run/##yyhNz8zL@/8/NzEzT0OzuqAoM69EQ8kjNScnX0chPL8oJ0VRSdO69v//f/kFJZn5ecX/dXXz8nUTi9LLAA)
## [Husk](https://github.com/barbuz/Husk), 8 bytes
```
¨H◄⁰,ω]!
```
[Try it online!](https://tio.run/##yygtzv7//9AKj0fTWx41btA53xmr@P8/AA)
## [Hyper-Dimensional Brainfuck](https://github.com/Property404/hdbf), 76 bytes
```
+[+[<<<+>>>>]+<-<-<<<+<++]<<.<++.<++..+++.<<++.<---.>>.>.+++.------.>-.>>--.
```
[Try it online!](https://tio.run/##HYjRCcAwEEIHEp1AXCTkJ5TS/Re4Xk6Rp37PeauwsGwjrQ2z3cvAttWYCLfMIqlEmYsj5V7Nqh8)
## [I](https://github.com/mlochbaum/ILanguage), INVALID
## [Icon](https://github.com/gtownsend/icon), 43 bytes
```
procedure main()
write("Hello, World!")
end
```
[Try it online!](https://tio.run/##y0zOz/v/v6AoPzk1pbQoVSE3MTNPQ5OrvCizJFVDySM1JydfRyE8vygnRVFJkys1L@X/fwA)
## [Idris](https://www.idris-lang.org/), 36 bytes
```
main:IO()
main=putStr"Hello, World!"
```
[Try it online!](https://tio.run/##y0wpyiz@/z83MTPPytNfQ5MLxLItKC0JLilS8kjNycnXUQjPL8pJUVT6/x8A)
## [Implicit](https://github.com/aaronryank/Implicit), 14 bytes
```
«Hello, World!
```
[Try it online!](https://tio.run/##K87MLchJLS5JTM7@///Qao/UnJx8HYXw/KKcFMX//wE)
## [Incident](https://github.com/TryItOnline/incident), 2080 bytes
```
A1.A2.A3,A4.A5,A6,A7;A8;B1;B2,B3.B4,B5;B6.B7.B8;C1,C2.C3;C4.C5,C6;C7,:C8.D1;D2,D3.D4,D5.D6;D7.D8,E1;E2;E3;E4,E5,E6.E7,E8.F1;F2.F3.F4,F5.F6;:F7.F8;G1,G2;G3,G4;G5.G6.G7.G8;H1.H2;H3.H4.H5.H6,H7;H8;I1,I2.I3;I4,I5.:I6,I7.I8,J1;J2,J3,J4,J5;J6;J7.J8;K1;K2;K3;K4,K5,K6;K7.K8,L1;L2,L3;L4,:L5;L6;L7,L8,M1.M2.M3.M4,M5,M6,M7,M8,N1.N2;N3,N4.N5;N6,N7.N8,Z4;a1,a1.:Z3.A1,a1;a2,a2,A1,A2.a2,a3.a3.A2,A3,a3.a5,a5,A3;A5.a5,a6,a6.A5;A6.a6.:a8.a8.A6;A8.a8;b2,b2.A8;B2.b2,b4.b4,B2,B4;b4.b5;b5;B4;B5;b5.b8.b8,B5.:B8.b8.c1;c1,B8,C1;c1,c2,c2;C1;C2,c2.c5,c5;C2,C5,c5.c8.c8,C5;C8;c8,d1;:d1.C8,D1;d1.d2;d2.D1.D2.d2.d5,d5,D2.D5.d5.d8,d8;D5;D8.d8,e5.e5.D8;E5,:e5,e8,e8,E5,E8;e8,f1.f1.E8.F1;f1;f2,f2;F1.F2.f2;f5.f5;F2;F5,f5;f7;f7.:F5,F7,f7;f8.f8;F7.F8,f8,g1;g1.F8;G1.g1,g2;g2.G1,G2,g2,g3;g3;G2,G3;g3,:g4,g4.G3;G4.g4.g5.g5,G4,G5.g5;g7;g7.G5;G7,g7,g8;g8.G7,G8;g8;h4.h4,G8;:H4,h4;h8,h8,H4.H8,h8.i5.i5;H8;I5;i5.i8;i8.I5,I8,i8.j1;j1;I8,J1;j1.j3.:j3;J1,J3;j3;j4,j4.J3,J4.j4,j8,j8.J4;J8,j8.k1.k1.J8.K1,k1,k2.k2;K1,K2;:k2.k5;k5;K2,K5.k5,k8;k8,K5.K8,k8;l1,l1;K8;L1;l1,Z1;Z2;Z2,Z3.Z2;Z1.Z1,:l2;l2;L1;L2,l2;l4.l4.L2.L4;l4.l5.l5.L4;L5;l5.l8.l8,L5.L8;l8;m2;m2.L8;:M2.m2,m3,m3,M2,M3,m3;m4.m4.M3;M4.m4,m5.m5.M4,M5,m5;m7,m7.M5.M7;m7.m8.:m8,M7,M8,m8,n1;n1.M8,N1;n1.n3,n3;N1;N3,n3.n5,n5;N3,N5;n5,n6.n6.N5.N6.:n6,n7;n7;N6.N7;n7.n8,n8;N7,N8;n8,a4,a4;Z3;A4,a4;a7.a7.A4.A7;a7,b1.b1;:A7;B1,b1;b3;b3,B1,B3.b3,b6.b6;B3;B6,b6;b7;b7,B6,B7,b7;c3,c3.B7,C3,c3.:c4.c4,C3,C4.c4;c6.c6,C4,C6.c6;c7,c7;C6.C7,c7.d3;d3.C7,D3,d3;d4;d4.D3,:D4,d4;d6,d6,D4,D6.d6;d7,d7,D6,D7.d7,e1,e1;D7,E1.e1,e2,e2;E1;E2,e2.e3;:e3,E2,E3,e3.e4;e4.E3.E4;e4,e6;e6;E4,E6,e6.e7.e7;E6.E7.e7,f3,f3.E7,F3;:f3.f4;f4,F3;F4,f4;f6;f6.F4.F6,f6,g6.g6;F6.G6.g6.h1;h1;G6;H1,h1.h2;h2.:H1;H2,h2.h3,h3,H2,H3,h3.h5.h5;H3,H5;h5;h6;h6;H5.H6.h6,h7.h7.H6,H7.h7;:i1,i1,H7.I1,i1.i2;i2;I1;I2,i2,i3.i3,I2,I3.i3;i4;i4;I3,I4,i4.i6,i6,I4.:I6,i6.i7.i7,I6;I7;i7.j2;j2;I7.J2;j2,j5;j5.J2.J5;j5.j6,j6.J5,J6,j6;j7;:j7;J6,J7.j7;k3,k3;J7.K3.k3.k4.k4,K3.K4;k4,k6;k6,K4.K6;k6,k7.k7;K6,K7.:k7,l3.l3.K7;L3;l3.l6;l6,L3;L6,l6;l7,l7,L6;L7.l7,m1.m1,L7;M1;m1,m6;m6,:M1;M6,m6;n2;n2;M6,N2,n2;n4.n4,N2;N4,n4.N8.N4,Z4,Z4
```
[Try it online!](https://tio.run/##LZXdbvJKDEVfyLI0/6PsKwgQkkAeoHcl/FO4@t6/Zzs90qq0PEoi1Nm2H5/5cb58/v3@rpyuvK6CrKKukqyyrApWFWuHtZd10HWUdcI667rouqJ10nptA9qobZI2oy3StFU3Dhsvm6CbKJukm4xN0U2VrcPWYxuwjbJNss26LbKtunPYed0F3UXZJd1lNLuiu4rOSefRBekiuqRd1q5oV7F3uvfYB91H3SfdZ9kX7Ct6J73XPqCP0idt@ix90b7K4DB4GYIMUYaEIWMoOlSMDqPHGDBGGZOMGWPRscrB4eDlEHCI0hwSDhmHIocqR6dHr8egxyjHJMcsxyLHKpPTyWMKMkWdEqYsU9GpylfEt5Nvp81X0JUZvr0QOv/Z5kHJiidh8SRkFbBKi2fC28AqK6X5rkpWmfdCwcnLiVfGO/JqHvXEO@JlRZgnEPraRE@V8Aa1WZvp7DA7WVdpF5k94aWiNdE5yZzMWxOd@Tyf5EkF5ezQnJ22VXjZlLPH2fPidePpek5C6Lz@M@ELFZuETTW/JCWbCoaguSS5VMMSUUG5OiV/ubgSL1ePnVNmhHJNek3MC3ZJKNdCtGGxK2JF1WvFEh@5Vrk53NxflPTm5OZx87rEii63AELvTKS5RblFZdFFpdwSYfakM8GtEO0SuiI3UnGrDKR0JrhHvUfzZh/lHnGvQiygJvpIZMlognnFo2qfhOGkPB3IX1CfTp9Bm2fA4BhZUJ5RnlGX@Kp5JTpEDIu8nDFUHZ28iNcXM@2EyW6sSCCjZ8Dp8qp4VXPGnP7j5IdNUMHI078cvjwRxtXE6ZeT5seD/DWFeVRy8HqIiyeDzkYxr0QOPOHXK96emDdsnLeXdzCOXo4meEclx4CjibyTkr/meie8i7yLHnlS6Pqu2rzr/y1H@Th82JDWfiafIJ8A@mSinySftPRkgnlWMiWd2EefLJ8CwmIy0Q8/VzEVmSro35Hgi324yHdRYoOx0OXk9MQOYLF2LHAKROickpRT1lPGOnBW0nEqROhrvlkwB5k5TIu0izRz1Dla0ZpgzjpnOgcqBXORuYDemug54BzMN0HMI1F6w1lrRRZiczfrOeNchGx4wjeLXBzhMOYkVnNPsExlil4CmksQFtsgl6CXiEvUbdCtiVwyiI3uTNdLIVhmOEWugdg83/ErtGvENVrBmW6eCec7h7tcs9yy3jJ22UY6/e5AuszBLnend4@712bvsPdCuwch9L2J3hPh9Jd9AuWejWUN6D3LvShZVgIFzcMJYdGb6MOD9Gw2Lw8S9BG4NKQ3wSMaPU@iPKI@spA@LpvkkfVRiPQZfQH96UG4YQYTeSY8E12HRZ5Znpkugwme/C38Y8HVQ3kFeQVbQ2PQF4lE6GME5ZXxyjJGHRd5FX0VjDzhrHsV@QlKxgKuKPOMn7ysqyzmfIDbynaWUt5O304OBUcHyjvjnaVhwe3F4uMN@uTFPOonii2zKPSpKuXL@P39Dw)
## [INTERCAL](http://www.catb.org/~esr/intercal/), 248 bytes
```
PLEASEDO,1<-#13PLEASEDO,1SUB#1<-#238PLEASEDO,1SUB#2<-#108PLEASEDO,1SUB#3<-#112DO,1SUB#4<-#256DO,1SUB#5<-#64DO,1SUB#6<-#194DO,1SUB#7<-#48DO,1SUB#8<-#26DO,1SUB#9<-#244DO,1SUB#10<-#168DO,1SUB#11<-#24DO,1SUB#12<-#16DO,1SUB#13<-#162DOREADOUT,1DOGIVEUP
```
[Try it online!](https://tio.run/##XY7BCoMwEEQ/xquCm8Q1ghdLQikUImp6L@JBKD2U/n@aDWSlHt/MPJj9/d0@6/MVwni3w2yNK6GvCpAHzv5SUCak/g8FDetTKCkEkVGR2GDGJiKqTEjbjrGNqHQmTSaLHZHiKdSkIo8hHTzqdI1lSKcwnprsYJxfSjDuentYP4bwAw)
## [Io](http://iolanguage.org/), 20 bytes
```
"Hello, World!"print
```
[Try it online!](https://tio.run/##y8z//1/JIzUnJ19HITy/KCdFUamgKDOv5P9/AA)
## [J](http://jsoftware.com/), 19 bytes
```
echo'Hello, World!'
```
[Try it online!](https://tio.run/##y/r/PzU5I1/dIzUnJ19HITy/KCdFUf3/fwA)
## [J-uby](https://github.com/cyoce/J-uby), 19 bytes
```
puts"Hello, World!"
```
[Try it online!](https://tio.run/##y9ItTar8/7@gtKRYySM1JydfRyE8vygnRVHp/38A)
## [Japt](https://github.com/ETHproductions/japt), 12 bytes
```
`HÁM, World!
```
[Try it online!](https://tio.run/##y0osKPn/P8HjcKOvjkJ4flFOiuL//wA)
## [Java (OpenJDK 8)](http://openjdk.java.net/), 76 bytes
```
interface H{static void main(String[]a){System.out.print("Hello, World!");}}
```
[Try it online!](https://tio.run/##DchBDkAwEADAr5QTCT7gA707OIjDRpdsVVdqSaTp28scx8IDLZ/ordlzJi8YVlhQ6XgJCC3qYTLqAPLVIIH8Ns1Qx@G9BI@Ob@nOP6UqNTrHjRo5OFOUdZ9Szh8)
## [Java (JDK 10)](http://jdk.java.net/), 76 bytes
```
interface H{static void main(String[]a){System.out.print("Hello, World!");}}
```
[Try it online!](https://tio.run/##y0osS9TNSsn@/z8zryS1KC0xOVXBo7q4JLEkM1mhLD8zRSE3MTNPI7ikKDMvPTo2UbM6uLK4JDVXL7@0RK8AKFiioeSRmpOTr6MQnl@Uk6KopGldW/v/PwA)
## [JavaScript (Babel Node)](https://babeljs.io/), 28 bytes
```
console.log('Hello, World!')
```
[Try it online!](https://tio.run/##y0osSyxOLsosKNFNSkxKzdHNy09J/f8/OT@vOD8nVS8nP11D3SM1JydfRyE8vygnRVFd8/9/AA)
## [JavaScript (Node.js)](https://nodejs.org), 28 bytes
```
console.log('Hello, World!')
```
[Try it online!](https://tio.run/##y0osSyxOLsosKNHNy09J/f8/OT@vOD8nVS8nP11D3SM1JydfRyE8vygnRVFd8/9/AA)
## [JavaScript (SpiderMonkey)](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey/Releases/45), 20 bytes
```
print`Hello, World!`
```
[Try it online!](https://tio.run/##y0osSyxOLsosKNEtLshMSS3Kzc/LTq38/7@gKDOvJMEjNScnX0chPL8oJ0Ux4f9/AA)
## [Jelly](https://github.com/DennisMitchell/jelly), 8 bytes
```
“3ḅaė;œ»
```
[Try it online!](https://tio.run/##y0rNyan8//9RwxzjhztaE49Mtz46@dDu//8B)
## [Jellyfish](https://github.com/iatorm/jellyfish), 15 bytes
```
P"Hello, World!
```
[Try it online!](https://tio.run/##y0rNyalMyyzO@P8/QMkDyMnXUQjPL8pJUfz/HwA)
## [Joy](http://www.latrobe.edu.au/humanities/research/research-projects/past-projects/joy-programming-language), 41 bytes
```
"Hello, World!"putchars.
quit
```
[Try it online!](https://tio.run/##y8qv/P9fySM1JydfRyE8vygnRVGpoLQkOSOxqFiPq7A0s@T/fwA)
## [jq](https://stedolan.github.io/jq/), 15 bytes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##yyr8/1/JIzUnJ19HITy/KCdFUen//3/5BSWZ@XnF/3V180pzcnQz8wpKS4CcosRy3fzSEiAHAA)
## [Julia 0.4](http://julialang.org/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##yyrNyUz8/7@gKDOvREPJIzUnJ19HITy/KCdFUUnz/38A)
## [Julia 0.5](http://julialang.org/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##yyrNyUw0/f@/oCgzr0RDySM1JydfRyE8vygnRVFJ8/9/AA)
## [Julia 0.6](http://julialang.org/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##yyrNyUw0@/@/oCgzr0RDySM1JydfRyE8vygnRVFJ8/9/AA)
## [Jx](http://www.2bestsystems.com/foundation/j/jx1/), 19 bytes
```
echo'Hello, World!'
```
[Try it online!](https://tio.run/##y6r4/z81OSNf3SM1JydfRyE8vygnRVH9/38A)
## [K (Kona)](https://github.com/kevinlawler/kona), 18 bytes
```
`0:"Hello, World!"
```
[Try it online!](https://tio.run/##y9bNzs9L/P8/wcBKySM1JydfRyE8vygnRVHp/38A)
## [K (oK)](https://github.com/JohnEarnest/ok), 20 bytes
```
{}`0:"Hello, World!"
```
[Try it online!](https://tio.run/##y9bNz/7/v7o2wcBKySM1JydfRyE8vygnRVHp/38A)
## [K (ngn/k)](https://github.com/ngn/k), 18 bytes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##y9bNS8/7/9/QQckjNScnX0chPL8oJ0VRyfr/fwA)
## [kavod](https://github.com/ConorOBrien-Foxx/kavod), 44 bytes
```
72#101#108><><##111><#44#32#87##114##100#33#
```
[Try it online!](https://tio.run/##y04sy0/5/9/cSNnQwBCILexs7GyUlQ0NDYGUiYmysZGyhTmIbwIkDAyUjY2V//8HAA)
## [Klein](https://github.com/Wheatwizard/Klein), 16 bytes
```
"Hello, World!"@
```
[Try it online!](https://tio.run/##y85Jzcz7/1/JIzUnJ19HITy/KCdFUcnh////BgYG/3UdAQ)
## [Kotlin](https://kotlinlang.org), 49 bytes
```
fun main(a:Array<String>){print("Hello, World!")}
```
[Try it online!](https://tio.run/##y84vycnM@/8/rTRPITcxM08j0cqxqCix0ia4pCgzL91Os7oASJdoKHmk5uTk6yiE5xflpCgqadb@/w8A)
## [ksh](http://www.kornshell.com/), 18 bytes
```
echo Hello, World!
```
[Try it online!](https://tio.run/##yy7O@P8/NTkjX8EjNScnX0chPL8oJ0Xx/38A)
## [Labyrinth](https://github.com/m-ender/labyrinth), 40 bytes
```
72.10:1.:8:..:):1:.#2#4..:1..4.:8.0.33.@
```
[Try it online!](https://tio.run/##y0lMqizKzCvJ@P/f3EjP0MDKUM/KwkpPz0rTytBKT9lI2QTINtTTMwEK6xnoGRvrOfz/DwA)
## [Lean](https://leanprover.github.io/), 21 bytes
```
#print"Hello, World!"
```
[Try it online!](https://tio.run/##y0lNzPv/X7mgKDOvRMkjNScnX0chPL8oJ0VR6f9/AA)
## [Lily](http://fascinatedbox.github.io/lily/), 33 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##y8nMqfz/v6AoM69EQ8kjNScnX0chPL8oJ0VRSfP/fwA)
## [Literate Haskell](https://www.haskell.org/onlinereport/literate.html), 27 bytes
```
>main=putStr"Hello, World!"
```
[Try it online!](https://tio.run/##y0gszk7NydHNySxJLUosSf3/3y43MTPPtqC0JLikSMkDKJevoxCeX5SToqj0/z8A)
## [LLVM IR](http://llvm.org/docs/LangRef.html), 141 bytes
```
@s=global[13x i8]c"Hello, World!"declare i8@puts([13x i8]*)define i8@main(){call i8@puts([13x i8]*@s)ret i8 0}
```
[Try it online!](https://tio.run/##y8kpy/3/36HYNj0nPykxJ9rQuEIh0yI2WckjNScnX0chPL8oJ0VRKSU1OSexKBUo5VBQWlKsAVOnpZmSmpaZB5bITczM09CsTk7MycFU51CsWZRaAmQqGNT@/w8A)
## [LNUSP](https://github.com/TryItOnline/lnusp), 349 bytes
```
  1 \  !!
  2  XX  !
  1 !  !!
 33 +
  1 *
100 +
  1 *
108 +
  1 *
114 +
  1 *
111 +
  1 *
 87 +
  1 *
 32 +
  1 *
 44 +
  1 *
111 +
  1 *
108 +
  1 *
108 +
  1 *
101 +
  1 *
 55 +
 16 +                    ?--?@              !
  1 +                   ?@ | ?
  1 *                   | +| *
  1 !                   ?  ! ?
  1  !-------------------?-@?
```
[Try it online!](https://tio.run/##bZBBDoUgDET3nGLYSkis6NddPYYLj2CMiXHH3fkgRiDS1et0Og1s@3UezgGEFZBSAB2wLJ5FEGUUjYG6@0ZQ22Y8JaY@Y3oZ05jYdIn7ur/ILDjLHIbA9INCpVhrnkspvqbm9k4LjsGVsYWy4WL8i@@2j362IfW3WM/s3B8)
## [Locksmith](https://github.com/ConorOBrien-Foxx/Locksmith), 79 bytes
```
070271709020871170700119081709707090317090404719030271908077197090319990303719
```
[Try it online!](https://tio.run/##JYrBDYAwDANXurSV3MzDBwSIB@wfEnjZvvNxLft9bs8agWgy4TSmLJvAzJkFazn984Oh5L3@qVHGb90L99wRLw)
## [Logicode](https://github.com/LogicodeLang/Logicode), 120 bytes
```
var l=@1101100out@1001000+@1100101+l+l+@1101111+@101100+@100000+@1010111+@1101111+@1110010+l+@1100100+@100001
```
[Try it online!](https://tio.run/##y8lPz0zOT0n9/78ssUghx9bB0NAAiAzyS0scgBQQGWiDxIAsQ@0cIIQoMDQEMsAKQbQBRJUBWAZZBUQjVJcBQrXh//8A)
## [LOLCODE](http://lolcode.org/), 37 bytes
```
HAI 1
VISIBLE "Hello, World!"
KTHXBYE
```
[Try it online!](https://tio.run/##y8nPSc5PSf3/38PRU8GQK8wz2NPJx1VBySM1JydfRyE8vygnRVGJyzvEI8Ip0vX/fwA)
## [Lost](https://github.com/Wheatwizard/Lost), 45 bytes
```
v<<<<<<<<<<>>>>>>>>>>>
>%?"Hello, WorldvU"-+@
```
[Try it online!](https://tio.run/##y8kvLvn/v8wGDuwQgMtO1V7JIzUnJ19HITy/KCelLFRJV9vh////uo4A)
## [LOWER](https://github.com/ConorOBrien-Foxx/LOWER), 177 bytes
```
ₔₓ₇₂ₔₓ₁₀₁ₐ₌₁₀₈ₔₓₐₔₓₐₔₓ₁₁₁ₔₓ₄₄ₔₓ₃₂ₔₓ₈₇ₔₓ₁₁₁ₔₓ₁₁₄ₔₓₐₔₓ₁₀₀ₔₓ₃₃
```
[Try it online!](https://tio.run/##y8kvTy36//9R05RHTZMfNbU/amqCsRsfNTWAyQmPmnpg3A6Y7AQMRiMMQbgtYARhNyMZ2wG2BasWCLsFm8kNYAQ3rfn/fwA)
## [Lua](https://www.lua.org), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##yylN/P@/oCgzr0TJIzUnJ19HITy/KCdFUen/fwA)
## [Ly](https://github.com/LyricLy/Ly), 17 bytes
```
"Hello, World!"&o
```
[Try it online!](https://tio.run/##y6n8/1/JIzUnJ19HITy/KCdFUUkt//9/AA)
## [M](https://github.com/DennisMitchell/m), 14 bytes
```
“Hello, World!
```
[Try it online!](https://tio.run/##y/3//1HDHI/UnJx8HYXw/KKcFMX//wE)
## [M4](https://www.gnu.org/software/m4/m4.html), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##yzX5/98jNScnX0chPL8oJ0Xx/38A)
## [MachineCode](https://github.com/aaronryank/MachineCode), 54 bytes
```
e80d00000H656c6c6f2c20576f726c6421596a1[6adZ6a4Xcd80c3
```
[Try it online!](https://tio.run/##y01MzsjMS03OT0n9/z/VwiDFAAQ8zEzNkoEwzSjZyMDU3CzN3AjIMzEyNLU0SzSMNktMiTJLNIlITrEwSDb@/x8A)
## [Make](https://www.gnu.org/software/make/), 28 bytes
```
a:
	@:$(info Hello, World!)
```
[Try it online!](https://tio.run/##y03MTv3/P9GKi9PBSkUjMy8tX8EjNScnX0chPL8oJ0VR8/9/AA)
## [Malbolge](https://www.lscheffer.com/malbolge.shtml), 112 bytes
```
('&%:9]!~}|z2Vxwv-,POqponl$Hjihf|B@@>,=<M:9&7Y#VV2TSn.Oe*c;(I&%$#"mCBA?zxxv*Pb8`qo42mZF.{Iy*@dD'<;_?!\}}|z2VxSSQ
```
[Try it online!](https://tio.run/##y03MScrPSU/9/19DXU3VyjJWsa62psoorKK8TFcnwL@wID8vR8UjKzMjrcbJwcFOx9bG18pSzTxSOSzMKCQ4T88/VSvZWsNTTVVFWSnX2cnRvqqiokwrIMkioTDfxCg3yk2v2rNSyyHFRd3GOt5eMaYWYnpwcOD//wA)
## [MarioLANG](https://esolangs.org/wiki/MarioLANG), 235 bytes
```
+>+>)+)+)+++)++++((((-[!)>->.
+"+"===================#+".")
+++!((+++++++++)++++++)<.---+
++=#===================")---.
++((.-(.)).+++..+++++++.<---
 !+======================---
=#>++++++++++++++.).+++.-!>!
  =======================#=#
```
[Try it online!](https://tio.run/##bY6xDsIwDET3fEXiLLFOvi9o/CNMnRAStBL/LwUXyoDIsywP5zv7sT5v@33drmPA4Yqj8G60wC5F3ZwJAun/VAhFU2yX1vBFz7HQzBBqrxOvaKiRHIdojaoMD3lmcAk15YI@5RB7dfzAT4QVLynnuTFeqWO8AA)
## [Mascarpone](https://github.com/catseye/Mascarpone), 29 bytes
```
[!dlroW ,olleH]$.............
```
[Try it online!](https://tio.run/##y00sTk4sKsjPS/3/P1oxJacoP1xBJz8nJ9UjVkUPGfz/DwA)
## [Mathics](http://mathics.github.io/), 21 bytes
```
Print@"Hello, World!"
```
[Try it online!](https://tio.run/##y00sychMLv7/P6AoM6/EQckjNScnX0chPL8oJ0VR6f9/AA)
## [MATL](https://github.com/lmendo/MATL), 15 bytes
```
'Hello, World!'
```
[Try it online!](https://tio.run/##y00syfn/X90jNScnX0chPL8oJ0VR/f9/AA)
## [Maverick](https://github.com/ConorOBrien-Foxx/Maverick), 45 bytes
```
outc(32+40`69`76`76`79`12`0`55`79`82`76`68`1)
```
[Try it online!](https://tio.run/##y00sSy3KTM7@/z@/tCRZw9hI28QgwcwywdwMjCwTDI0SDBJMTUFMCyOQmJlFgqHm//8A)
## [Maxima](http://maxima.sourceforge.net/), 23 bytes
```
print("Hello, World!");
```
[Try it online!](https://tio.run/##y02syMxN/P@/oCgzr0RDySM1JydfRyE8vygnRVFJ0/r/fwA)
## [MaybeLater](https://github.com/TehFlaminTaco/MaybeLater), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##y02sTErNSSxJLfr/v6AoM69EySM1JydfRyE8vygnRVHp/38A)
## [Milky Way](https://github.com/zachgates/Milky-Way), 16 bytes
```
"Hello, World!"!
```
[Try it online!](https://tio.run/##y83Mya7ULU@s/P9fySM1JydfRyE8vygnRVFJ8f9/AA)
## [Minimal-2D](https://esolangs.org/wiki/Minimal-2D), 123 bytes
```
--->->-> D
 D+>>+>+>L
DD/+++<D/-<  L
>R++++ R>+++D
>D-->++++>  L
>R>+++<<<- /UU
R.>-->-.>..+>+D
D>-->+.+++>+++L
R>-.D
U/<<L
```
[Try it online!](https://tio.run/##JUwxCgRBCOt9hb3owNWSKuVUA/OAg2sWdu//3ZxyhEhiNM/1vZ737a/POe6OhlKUBlhhCjnMLDk8VadglTNdqEkB66cX@GetM9N17C0r0I2BiKqisK1FXxenrMooe2TOc34)
## [miniML](https://github.com/feresum/acml), 26 bytes
```
map putchar"Hello, World!"
```
[Try it online!](https://tio.run/##y83My8zN@f8/N7FAoaC0JDkjsUjJIzUnJ19HITy/KCdFUen/fwA)
## [Minkolang](https://github.com/elendiastarman/Minkolang), 18 bytes
```
"Hello, World!"$O.
```
[Try it online!](https://tio.run/##y83My87PScxL//9fySM1JydfRyE8vygnRVFJxV/v/38A)
## [Mirror](https://github.com/alexander-liao/mirror), 16 bytes
```
"Hello, World!"@
```
[Try it online!](https://tio.run/##y80sKsov@v9fySM1JydfRyE8vygnRVHJ4f9/AA)
## [Momema](https://github.com/ScratchMan544/momema), 63 bytes
```
0-9*072*0101*0108*0108*0111*044*032*087*0111*0114*0108*0100*033
```
[Try it online!](https://tio.run/##y83PTc1N/P/fQNdSy8DcSMvA0MAQRFjACEMg18REy8AYKGdhDhUwNDSBKzIAyhn//w8A)
## [Monkeys](https://github.com/TryItOnline/monkeys), 448 bytes
```
7 RIGHT
7 RIGHT
7 RIGHT
7 RIGHT
7 UP
5 DOWN
5 RIGHT
4 DOWN
7 TEACH
7 BOND
4 UP
7 BOND
7 TEACH
7 TEACH
6 YELL
4 TEACH
4 TEACH
7 FIGHT
5 TEACH
6 YELL
7 TEACH
7 TEACH
5 FIGHT
6 YELL
6 YELL
7 TEACH
5 FIGHT
6 YELL
7 EGO
4 TEACH
5 TEACH
6 YELL
4 FIGHT
7 TEACH
6 YELL
4 TEACH
4 TEACH
4 DOWN
7 TEACH
4 UP
4 TEACH
5 FIGHT
6 YELL
4 TEACH
7 TEACH
6 YELL
7 TEACH
5 FIGHT
6 YELL
7 FIGHT
5 FIGHT
5 FIGHT
6 YELL
7 FIGHT
7 FIGHT
6 YELL
7 EGO
7 TEACH
7 TEACH
6 YELL
```
[Try it online!](https://tio.run/##y83Py06tLP7/31whyNPdI4QLNx0awGWq4OIf7gekIGImEK65Qoiro7MHkHby93MBigJVQtkIKQhtphDp6uMDVALhmsCl3cAGmqIqQ9dtClUGlUZThSZrruDq7g@3wRTdAW5QX@F1F5oHwT4zwW6dCXaf4nQczMOoNJq0OTYvYQ/T//8B)
## [Moonscript](https://moonscript.org/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##y83PzytOLsosKPn/v6AoM69EySM1JydfRyE8vygnRVHp/38A)
## [Mornington Crescent](https://github.com/padarom/esoterpret), 3568 bytes
```
Take Northern Line to Hendon Central
Take Northern Line to Bank
Take Circle Line to Bank
Take District Line to Gunnersbury
Take District Line to Victoria
Take Victoria Line to Seven Sisters
Take Victoria Line to Victoria
Take Circle Line to Victoria
Take Circle Line to Bank
Take Circle Line to Hammersmith
Take Circle Line to Cannon Street
Take Circle Line to Hammersmith
Take Circle Line to Cannon Street
Take Circle Line to Bank
Take Circle Line to Hammersmith
Take District Line to Upminster
Take District Line to Hammersmith
Take District Line to Upminster
Take District Line to Gunnersbury
Take District Line to Paddington
Take District Line to Acton Town
Take Piccadilly Line to Holloway Road
Take Piccadilly Line to Acton Town
Take District Line to Acton Town
Take District Line to Gunnersbury
Take District Line to Hammersmith
Take Circle Line to Notting Hill Gate
Take District Line to Upminster
Take District Line to Notting Hill Gate
Take District Line to Upminster
Take District Line to Victoria
Take Victoria Line to Seven Sisters
Take Victoria Line to Victoria
Take Circle Line to Victoria
Take District Line to Upminster
Take District Line to Gunnersbury
Take District Line to Mile End
Take District Line to Hammersmith
Take Circle Line to Notting Hill Gate
Take District Line to Upminster
Take District Line to Upminster
Take District Line to Mile End
Take District Line to Paddington
Take Circle Line to Paddington
Take District Line to Acton Town
Take Piccadilly Line to Heathrow Terminals 1, 2, 3
Take Piccadilly Line to Holborn
Take Central Line to Holborn
Take Central Line to Mile End
Take District Line to Upminster
Take District Line to Hammersmith
Take District Line to Upminster
Take District Line to Barking
Take District Line to Hammersmith
Take District Line to Upminster
Take District Line to Gunnersbury
Take District Line to Barking
Take District Line to Gunnersbury
Take District Line to Paddington
Take Circle Line to Paddington
Take Circle Line to Wood Lane
Take Circle Line to Victoria
Take Circle Line to Victoria
Take District Line to Gunnersbury
Take District Line to Hammersmith
Take District Line to Upminster
Take District Line to Gunnersbury
Take District Line to Paddington
Take Circle Line to Paddington
Take District Line to Mile End
Take Central Line to Fairlop
Take Central Line to Mile End
Take District Line to Barking
Take District Line to Upminster
Take District Line to Upminster
Take District Line to Hammersmith
Take Circle Line to Notting Hill Gate
Take District Line to Upminster
Take District Line to Mile End
Take District Line to Gunnersbury
Take District Line to Paddington
Take Circle Line to Paddington
Take Circle Line to Hammersmith
Take District Line to Mile End
Take District Line to Richmond
Take District Line to Mile End
Take District Line to Paddington
Take Circle Line to Paddington
Take District Line to Richmond
Take District Line to Bank
Take Circle Line to Hammersmith
Take District Line to Upminster
Take District Line to Stepney Green
Take District Line to Hammersmith
Take District Line to Stepney Green
Take District Line to Upney
Take District Line to Notting Hill Gate
Take Circle Line to Notting Hill Gate
Take Circle Line to Notting Hill Gate
Take District Line to Upminster
Take District Line to Upney
Take District Line to Upminster
Take District Line to Bank
Take Circle Line to Bank
Take Northern Line to Charing Cross
Take Bakerloo Line to Charing Cross
Take Bakerloo Line to Paddington
Take Circle Line to Bank
Take Circle Line to Bank
Take Northern Line to Mornington Crescent
```
[Try it online!](https://tio.run/##xVdLbsJADN33FHMAumh7gpK2sACE@LRrk1jNiMRGzlDE6akRn4pAGJIS2CBFz3ie7Wd7JmUhS9@O6TEUzEIkt1qNYIqmx@JiFDIdS2gcmzZSxGQCNRFIHk4bNYGmGyiwEiZ4AnizmRMbuj3UmhOhZJO5LAssPvWDxcIG3n3t4SH@IJmh/kvdFNgcusiROwsWhtSGNNUDU@vik3gARJqwoRNEV5OHy8kdJXU8Sy2tU1aA/9@Dv7B9iKKN/AoMXrUwZEa82Br0bRhCZJNk@ceTk4QXsDQDhqjQKu/Ie1KFaHzl7LFzGq1pKzPTAocV83otP7dtqxrk07V62jtFd66HD/fQzDdBjuVVegTBxcILM0JRrpBk5qlhnhvm5VxbTXQ5bClthv5loCfc@udOE2SqGbvjXDvPoPxc9EgiB38xR6YDhOWXnadlK8zAG2yNsg1zKNC8fD/ASsKzSto@X/f/zpFbzTNPkHXL1y8hD8GBDeOUC@Gax7Hn9BpvbEOHM8Klael1kSr35yVexmuLcreTy7Ra24Yu5uvfJt4nzdEzKIhB1rwD4Wx7dWrqj84VLmXj0WIVat39i09P3r34fgE)
## [MUMPS](http://www.cs.uni.edu/~okane/), 18 bytes
```
 w "Hello, World!"
```
[Try it online!](https://tio.run/##yy3NLSj@/1@hXEHJIzUnJ19HITy/KCdFUen/fwA)
## [MY](https://bitbucket.org/zacharyjtaylor/my-language), 60 bytes
```
27á'←1Aá'←8Aá'2×←1Bá'←44á'←2Ġ'←78á'←1Bá'←4Bá'←8Aá'←AȦ'←33á'←
```
[Try it online!](https://tio.run/##y638/9/I/PBC9UdtEwwdIbQFiDY6PB0k5AQRMjGB0EZHFoAocwuoDpi0E5JOIO14YhmIMjaGcP//BwA)
## [MY-BASIC](https://github.com/paladin-t/my_basic), 20 bytes
```
Print"Hello, World!"
```
[Try it online!](https://tio.run/##y63UTUoszkz@/z@gKDOvRMkjNScnX0chPL8oJ0VR6f9/AA)
## [Neim](https://github.com/okx-code/Neim), 16 bytes
```
(Hello, World!)B
```
[Try it online!](https://tio.run/##y0vNzP3/X8MjNScnX0chPL8oJ0VR0@n/fwA)
## [Neutrino](https://github.com/alexander-liao/neutrino), 15 bytes
```
"Hello, World!'
```
[Try it online!](https://tio.run/##y0stLSnKzMv//1/JIzUnJ19HITy/KCdFUf3/fwA)
## [Nhohnhehr](https://github.com/catseye/Nhohnhehr), 181 bytes
```
+-----------+
|$010010000\|
|1100101011\|
|0110001101\|
|1000110111\|
|1001011000\|
|0100000010\|
|1011101101\|
|1110111001\|
|0011011000\|
|1100100001\|
|00001@    \|
+-----------+
```
[Try it online!](https://tio.run/##y8vIz8jLSM0o@v9fWxcBtLlqVAwMDUDIwCCmhqvGEMwBQkMQzwDEBRFgHoxtCOMZQuQhKg3AwBBiCkgRQh9EkwGEBzUDxT4DuByQ4aAABEAeijv//wcA)
## [Nim](http://nim-lang.org/), 19 bytes
```
echo"Hello, World!"
```
[Try it online!](https://tio.run/##y8vM/f8/NTkjX8kjNScnX0chPL8oJ0VR6f9/AA)
## [NotQuiteThere](https://github.com/cairdcoinheringaahing/NotQuiteThere), 17 bytes
```
'Hello, World!'+0
```
[Try it online!](https://tio.run/##yyss@f9f3SM1JydfRyE8vygnRVFd2@D/fwA)
## [NTFJ (NTFJC)](https://github.com/ConorOBrien-Foxx/ntfjc), 106 bytes
```
~#~~#~~~@*~##~~#~#@*~##~##~~@::**~##~####@:*~~#~##~~@*~~#~~~~~@*~#~#~###@**~###~~#~@**~##~~#~~@*~~#~~~~#@*
```
[Try it online!](https://tio.run/##yytJy0r@/79OuQ6E6hy06pTBTGUIC8RxsLLSgnKUlR2stMDSymC1YD0QXWBBoC6QSrAJECZYCVwlUP7/fwA)
## [Numberwang](https://esolangs.org/wiki/Numberwang_(brainfuck_derivative)), 72 bytes
```
220200949409153121212000717002230663002330030931131130003633113112300093
```
[Try it online!](https://tio.run/##JYlRCoAwDEOvlCazo8dREL/cx0A8fu2QhPAeGc99nPPdx5VJgkC0aAjbZFwB0K0DpOCuAtUIIbPV@uX6hctCmR8)
## [Oasis](https://github.com/Adriandmen/Oasis), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##y08sziz@/1/JIzUnJ19HITy/KCdF8f9/AA)
## [Objective-C (clang)](http://clang.llvm.org/), 30 bytes
```
main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##y0/KSk0uySxL1U3WTc5JzEv//z83MTNPQ7O6oLSkWEPJIzUnJ19HITy/KCdFUUnTuvb//3/JaTmJ6cX/dcPz8nUTc3IA)
## [Objective-C (gcc)](https://gcc.gnu.org/onlinedocs/gcc-7.1.0/gcc/Objective-C.html), 30 bytes
```
main(){puts("Hello, World!");}
```
[Try it online!](https://tio.run/##y0/KSk0uySxL1U3WTU9O/v8/NzEzT0OzuqC0pFhDySM1JydfRyE8vygnRVFJ07r2/38A)
## [OCaml](http://www.ocaml.org/), 27 bytes
```
print_string"Hello, World!"
```
[Try it online!](https://tio.run/##y09OzM35/7@gKDOvJL64BEilK3mk5uTk6yiE5xflpCgq/f8PAA)
## [occam-pi](http://projects.cs.kent.ac.uk/projects/kroc/trac/), 83 bytes
```
#INCLUDE"course.module"
PROC H(CHAN BYTE so!)
  out.string("Hello, World!",0,so!)
:
```
[Try it online!](https://tio.run/##y09OTszVLcj8/1/Z08/ZJ9TFVSk5v7SoOFUvNz@lNCdViSsgyN9ZwUPD2cPRT8EpMsRVoThfUZNLQSG/tESvuKQoMy9dQ8kjNScnX0chPL8oJ0VRScdAB6zG6v9/AA)
## [Octave](https://www.gnu.org/software/octave/), 19 bytes
```
disp"Hello, World!"
```
[Try it online!](https://tio.run/##y08uSSxL/f8/JbO4QMkjNScnX0chPL8oJ0VR6f9/AA)
## [Ohm](https://github.com/nickbclifford/Ohm), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##y8/I/f9fySM1JydfRyE8vygnRfH/fwA)
## [Ohm v2](https://github.com/nickbclifford/Ohm), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##y8/INfr/X8kjNScnX0chPL8oJ0Xx/38A)
## [Pain-Flak](https://github.com/Cis112233/Pain-Flak), 152 bytes
```
)))))}{}{)))}{))(}{((((])][][][([(])()()([((]][[()()()(])}{][][)][(][([())(]][][][][][[))(]][[)][][)][][][][))(}{}{))))(}{)}{)}{))()()()((((((((((((}><{
```
[Try it online!](https://tio.run/##TU1JCsAwCPyOHvKDUug7xEMuhdCSBNqb5Ou1GnvojOA2jj2XmvYzH6roGDJkJkQYAgZGJieQleAkGzIRRMcm9r3JYKrskuPESdESfprgdJ@fvMAI/Bx/GOsiqk/rd2n10rS9)
## [OML](https://github.com/ConorOBrien-Foxx/OML), 16 bytes
```
"Hello, World!"s
```
[Try it online!](https://tio.run/##y8/N@f9fySM1JydfRyE8vygnRVGp@P9/AA)
## [oOo CODE](https://github.com/TryItOnline/brainfuck), 228 bytes
```
OoOoOoOoOoOooooooooooOoOooOooOooOooOoOOOoOoooOoooooOoooooooooooOoOoooOoOOoOoOOooooooOOooooOoOOoOOOooooOoOOoOOOoOOoOoOOoOOoOOOoooooooOoOOoOOOooooOooOooOooOOoooOooOOOoooOOOoOoOOoOOoOOOoOooOooOooOooOooOooOOoooOOooOOoooOooOOooOooOOo
```
[Try it online!](https://tio.run/##ZY5JDgAgCAOf2Eeo5/7/hAmroBKWdoiSXNxHBKybR4cnALPh7iCVsGQimOLogyvrIyP8QdMxFvv/im@LUUQu)
## [ORK](https://github.com/TryItOnline/ork), 80 bytes
```
When this program starts
I have a scribe called H.
H is to write "Hello, World!"
```
[Try it online!](https://tio.run/##DcrBDYAgDAXQu1N8ORvnwAk4V2yEWK0pjY6PvvNTO3pPhS94qQ236W50ojmZt2FBoYdBaNnqysgkwhviPET82xWvVWeEyCI6IanJNobePw)
## [OSH](https://www.oilshell.org/), 18 bytes
```
echo Hello, World!
```
[Try it online!](https://tio.run/##yy/O@P8/NTkjX8EjNScnX0chPL8oJ0Xx/38A)
## [Paradoc](https://github.com/betaveros/paradoc), 2 bytes
```
Hw
```
[Try it online!](https://tio.run/##K0gsSkzJT/7/36P8/38A)
## [Parenthetic](https://github.com/cammckinnon/Parenthetic), 604 bytes
```
((()()())(()())((()())((()()())(()(())))((()(())(())())((()(()()))((()()(()))((())()()()()()())((())()()()()()()()()()()()()()()()()()()()))((()()(()))(()()())((())()()()()()()()()()()()()()))(()(()))))))((()(()))((()())((())()()())((())()()()))((()())((())())((())))((()())((()))((())()()()()()()))((()())((()))((())()()()()()()))((()())((()))((())()()()))((()())((())()()()()())((())()()()()()))((()())((())()()()()()())((())()()()()))((()())((())()())((())()))((()())((()))((())()()()))((()())((()))((())))((()())((()))((())()()()()()()))((()())((())())((())()))((()())((())()()()()()())((())()()())))
```
[Try it online!](https://tio.run/##K0gsSs0ryUgtyUz@/19DQ0MTBDU1oCQSBRUFUlARiABcAVgFTC2MqamBBDFFcEM0k4jSj@RAJDci@wKLQ9DlITSqKBavkC2PzT1Y@TjUoYtgqoP7hEg3kONjXLbgcicQ/P8PAA)
## [Pari/GP](http://pari.math.u-bordeaux.fr/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##K0gsytRNL/j/v6AoM69EQ8kjNScnX0chPL8oJ0VRSfP/fwA)
## [Pascal (FPC)](https://www.freepascal.org/), 32 bytes
```
begin write('Hello, World!')end.
```
[Try it online!](https://tio.run/##K0gsTk7M0U0rSP7/Pyk1PTNPobwosyRVQ90jNScnX0chPL8oJ0VRXTM1L0Xv/38A)
## [PATH](https://sourceforge.net/projects/pathlang/), 113 bytes
```{%raw%}
/++}+++++++}+++++}<$+++++++<
\+}++}++++++{{{{{-^}++.}+++.+++++++..+++.}++.}++++.}+++.{{{.+++.------.--------.}}+.
{%endraw%}```
[Try it online!](https://tio.run/##K0gsyfj/X19bu1YbAiB0rY0KlG/DFQMSg0pXg4BuHJCnBxLRgyrSAzH0YKJQOaBKsLAuGEApIKO2Vlvv/38A)
## [pbrain](http://www.parkscomputing.com/applications/pbrain/), 87 bytes
```
--->->->>+>+>>+[++++[>+++[>++++>-->+++<<<-]<-]<+++]>>>.>-->-.>..+>++++>+++.+>-->[>-.<<]
```
[Try it online!](https://tio.run/##NUrLCcBQCBtIzASSRcRDe3uXUro/2PhK81GJuc/nWFe3u3NIE2lpQvIfRr21IsJrpLtIYnIHAftqMnY5FUdU9ws)
## [Perl 5](https://www.perl.org/), 18 bytes
```
say"Hello, World!"
```
[Try it online!](https://tio.run/##K0gtyjH9/784sVLJIzUnJ19HITy/KCdFUen//3/5BSWZ@XnF/3V9TfUMDAE)
## [Perl 6](https://perl6.org), 19 bytes
```
say "Hello, World!"
```
[Try it online!](https://tio.run/##K0gtyjH7/784sVJBySM1JydfRyE8vygnRVHp/38A)
## [Phoenix](https://github.com/senselogic/PHOENIX), 20 bytes
```
echo"Hello, World!";
```
[Try it online!](https://tio.run/##K8jIT83LrPj/PzU5I1/JIzUnJ19HITy/KCdFUcn6/38A)
## [Phooey](https://tio.run/##DcqxDkAwEADQX7l2ahPpD4jEaDMYzKQll7ROziGIby9vfjfOOa/7CNMCacDFWHUQ@ucYGKgSvmpMK7EYvYnX1iG5OUgnvt3F2PIPQO5klGB0E2KkAnri6JW25ZvzBw), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##K8jIz0@t/P9fySM1JydfRyE8vygnRfH/fwA)
## [PHP](https://php.net/), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##K8go@P/fIzUnJ19HITy/KCdF8f9/AA)
## [PicoLisp](http://picolisp.com/), 26 bytes
```
(prin"Hello, World!")(bye)
```
[Try it online!](https://tio.run/##K8hMzs/JLC74/1@joCgzT8kjNScnX0chPL8oJ0VRSVMjqTJV8/9/AA)
## [Piet](https://github.com/cincodenada/bertnase_npiet), 183 bytes
```
0000000: 47 49 46 38 37 61 1c 00 03 00 84 14 00 ff 00 00  GIF87a..........
0000010: 00 00 00 ff c0 c0 ff 00 00 c0 00 00 ff ff c0 ff  ................
0000020: ff 00 c0 c0 00 c0 ff c0 00 ff 00 00 c0 00 c0 ff  ................
0000030: ff 00 ff ff 00 c0 c0 c0 c0 ff 00 00 ff 00 00 c0  ................
0000040: ff c0 ff ff 00 ff c0 00 c0 ff ff ff ff ff ff ff  ................
0000050: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
0000060: ff ff ff ff ff ff ff ff ff ff ff ff ff 2c 00 00  .............,..
0000070: 00 00 1c 00 03 00 00 05 3c e0 23 42 4a 73 24 c3  ........<.#BJs$.
0000080: 23 39 ec 33 35 f0 02 39 d1 c2 3c 81 11 44 82 63  #9.35..9..<..D.c
0000090: 2a 40 05 42 70 98 10 24 13 c1 44 f4 80 2c 17 0a  *@.Bp..$..D..,..
00000a0: 43 21 32 a9 56 0f 0d 87 80 3a 39 20 1c 12 c3 20  C!2.V....:9 ...
00000b0: 5c 28 17 72 21 00 3b                             \(.r!.;
```
[Try it online!](https://tio.run/##ldLNTgMhEAfwu0/xb9qDMYYAwy5QPZhqNPoAnnqhtJt4a9T3X2cWl641bZQQQvj4MQPs33affa9LWcJ5uAjXggLIozUwGVpDk7TBwTjpdN0wqIGn58fgk6rlYoAMU2VBWZy11LorT6bKLLdQR6VQlqmyMY8b82jqX@ZZiipVzq3mUXhT8wTlCpUnVA2pDh7VE1RTqH/VE1T7d8rm8QV/ONcj5esLTj@A1AaUsdOwBGfhEjzBOmQ6ULdqvnr5WHxTgSleTBG7DOJOg44dKyNbg2wFDPzTDJxDsGiZmkdFjVJRMPWgcqGiUAluCINP9xoxwGgJwBDyIHSMaEnQeOgEXN2p1V6phTiHBJP8do7cgCxSRNNC8ztuEbxspyTh2SF9YyU77uN@ZtWrZLiMqLe@YanJsEEO9FZIvifa4FxZX6r3mbrp@y8)
## [Pike](https://pike.lysator.liu.se/), 35 bytes
```
int main(){write("Hello, World!");}
```
[Try it online!](https://tio.run/##K8jMTv3/PzOvRCE3MTNPQ7O6vCizJFVDySM1JydfRyE8vygnRVFJ07r2/38A)
## [PingPong](https://github.com/graue/esofiles/tree/master/pingpong), 32 bytes
```
$!dlroW$ $,\
@/=\#Hello /
 \./
```
[Try it online!](https://tio.run/##K8jMSy/Iz0v//19FMSWnKD9cRUFFJ4bLQd82RtkjNScnX0GfSyFGT///fwA)
## [Pip](https://github.com/dloscutoff/pip), 15 bytes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##K8gs@P9fySM1JydfRyE8vygnRVHp/38A)
## [pl](https://github.com/quartata/pl-lang), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##K8j5/98jNScnX0chPL8oJ0Xx/38A)
## [Pony](https://www.ponylang.org/), 62 bytes
```
actor Main new create(env:Env)=>env.out.print("Hello, World!")
```
[Try it online!](https://tio.run/##K8jPq/z/PzG5JL9IwTcxM08hL7VcIbkoNbEkVSM1r8zKNa9M09YOyNLLLy3RKyjKzCvRUPJIzcnJ11EIzy/KSVFU0vz/HwA)
## [Positron](https://github.com/alexander-liao/positron), 21 bytes
```
print@"Hello, World!"
```
[Try it online!](https://tio.run/##K8gvziwpys/7/7@gKDOvxEHJIzUnJ19HITy/KCdFUen/fwA)
## [PostL](https://github.com/alexander-liao/postfix-lang), 16 bytes
```
"Hello, World!".
```
[Try it online!](https://tio.run/##K8gvLsn5/1/JIzUnJ19HITy/KCdFUUnv/38A)
## [PostScript (xpost)](https://github.com/luser-dr00g/xpost), 21 bytes
```
(Hello, World!)=
quit
```
[Try it online!](https://tio.run/##K8gvLilOLsosKNGtKACy///X8EjNycnXUQjPL8pJUdS05SoszQQKAwA)
## [PowerShell](https://github.com/TryItOnline/TioSetup/wiki/Powershell), 15 bytes
```
'Hello, World!'
```
[Try it online!](https://tio.run/##K8gvTy0qzkjNyfn/X90DSOXrKITnF@WkKKr//w8A)
## [PowerShell Core](https://github.com/PowerShell/PowerShell), 15 bytes
```
'Hello, World!'
```
[Try it online!](https://tio.run/##K8gvTy0qzkjNydFNzi9K/f9f3QPIztdRCM8vyklRVP//HwA)
## [Prelude](https://esolangs.org/wiki/Prelude), 38 bytes
```
92480969393782833909095806(^+^+^^+++!)
```
[Try it online!](https://tio.run/##KyhKzSlNSf3/39LIxMLA0szS2NLY3MLIwtjY0gAITS0MzDTitIEwTltbW1Hz/38A)
## [Premier](https://github.com/ConorOBrien-Foxx/Premier), 14 bytes
```

Hello, World!
```
[Try it online!](https://tio.run/##KyhKzc1MLfr/n8sjNScnX0chPL8oJ0Xx/38A)
## [Preproc](https://gitlab.com/pavelb/Preproc), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##KyhKLSjKT/7/3yM1JydfRyE8vygnRfH///9uPo7uVroBAA)
## [Prolog (Ciao)](https://ciao-lang.org/), 29 bytes
```
main:-write('Hello, World!').
```
[Try it online!](https://tio.run/##KyjKz8lP103OTMz//z83MTPPSre8KLMkVUPdIzUnJ19HITy/KCdFUV1T7/9/AA)
## [Prolog (SWI)](http://www.swi-prolog.org), 25 bytes
```
?-write('Hello, World!').
```
[Try it online!](https://tio.run/##KyjKz8lP1y0uz/z/3163vCizJFVD3SM1JydfRyE8vygnRVFdU@//fwA)
## [Proton](https://github.com/alexander-liao/proton), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##KyjKL8nP@/@/oCgzr0RDySM1JydfRyE8vygnRVFJ8/9/AA)
## [Proton 2.0](https://github.com/alexander-liao/proton-2.0), 21 bytes
```
print@"Hello, World!"
```
[Try it online!](https://tio.run/##KyjKL8nPM/r/v6AoM6/EQckjNScnX0chPL8oJ0VR6f9/AA)
## [Pure](https://github.com/agraef/pure-lang), 33 bytes
```
using system;puts"Hello, World!";
```
[Try it online!](https://tio.run/##KygtSv3/v7Q4My9dobiyuCQ117qgtKRYySM1JydfRyE8vygnRVHJ@v9/AA)
## [PureScript](http://www.purescript.org/), 79 bytes
```
module Main where
import Control.Monad.Eff.Console(log)
main=log"Hello, World!"
```
[Try it online!](https://tio.run/##DcuxCoAgFEbh3aewpoLwDZoiaHFujryWcPWXm9Hjm9vhg5NfoeeUkEutEe5l0vYISX83CakQM6ToBakI2Fikw5nVe9PkAdPAuEYV2zC36jdixqR3CLuur/UH)
## [Purple](https://esolangs.org/wiki/Purple), 62 bytes
```
AA1AA1AA1bA1b1Bo1bb1bbibb1Bi1b     
 ! d l r o W   , o l l e H
```
[Try it online!](https://tio.run/##KygtKshJ/f/f0dEQgpKAyNAp3zApCYgygaRTpmGSAghwKSgqpCjkKBQp5CuEA/k6QDoHCFMVPP7/BwA)
## [Pushy](https://github.com/FTcode/Pushy), 16 bytes
```
`Hello, World!`"
```
[Try it online!](https://tio.run/##Kygtzqj8/z/BIzUnJ19HITy/KCdFMUHp/38A)
## [Pyke](https://github.com/muddyfish/PYKE), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##K6jMTv3/X8kjNScnX0chPL8oJ0Xx/38A)
## [Pylons](https://github.com/morganthrapp/Pylons-lang), 16 bytes
```
"Hello, World!"c
```
[Try it online!](https://tio.run/##K6jMyc8r/v9fySM1JydfRyE8vygnRVEp@f9/AA)
## [Pyon](https://github.com/alexander-liao/pyon), 20 bytes
```
print("Hello, World!
```
[Try it online!](https://tio.run/##K6jMz/v/v6AoM69EQ8kjNScnX0chPL8oJ0Xx/38A)
## [Pyramid Scheme](https://github.com/ConorOBrien-Foxx/Pyramid-Scheme), 857 bytes
```
  ^      ^      ^     ^      ^      ^      ^      ^      ^      ^      ^      ^      ^
 / \    / \    / \   / \    / \    / \    / \    / \    / \    / \    / \    / \    / \
/out\  /out\  /out\ /out\  /out\  /out\  /out\  /out\  /out\  /out\  /out\  /out\  /out\
-----^ -----^ -----^----- ^----- ^----- ^----- ^----- ^----- ^----- ^----- ^----- ^-----
    / \    / \    / \    / \    / \    / \    / \    / \    / \    / \    / \    / \
   /chr\  /chr\  /chr\  /chr\  /chr\  /chr\  /chr\  /chr\  /chr\  /chr\  /chr\  /chr\
  ^----- ^----- ^----- ^----- ^----- ^----- ^----- ^----- ^----- ^----- ^----- ^-----
 / \    / \    / \    / \    / \    / \    / \    / \    / \    / \    / \    / \
/72 \  /101\  /108\  /111\  /44 \  /32 \  /87 \  /111\  /114\  /108\  /100\  /33 \
-----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
```
[Try it online!](https://tio.run/##rZFBCoQwDEX3PcW/gLTRgh5GBFHBWYiDowtPX22chZVuismir/lJCj/97ks7ffrs143DNDgHNOAIENNSoKBR@1uAmJYGpedtPZMAMS0VKvPRIACfeAcFEeOPNXh041KL4nxVxPJzAeLudZn7RJOhCxWDOLOWa8XVUpW41YjsfcAY7izw/35AEM4d)
## [Pyt](https://github.com/mudkip201/pyt), 40 bytes
```
89*2ᴇ⁺Đ7+ĐĐ3+7²5-2⁵9²6+Đ4!+Đ3+Đ6-2ᴇĐ₃áƇǰ
```
[Try it online!](https://tio.run/##K6gs@f/fwlLL6OGW9keNu45MMNc@MuHIBGNt80ObTHWNHjVutTy0yQwoZqKoDRI@MsFMF6T2yIRHTc2HFx5rP77h/38A)
## [Pyth](https://github.com/isaacg1/pyth), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##K6gsyfj/X8kjNScnX0chPL8oJ0Xx/38A)
## [Python 1](https://www.python.org/download/releases/1.6.1/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##K6gsycjPM/z/v6AoM69EySM1JydfRyE8vygnRVHp/38A)
## [Python 2](https://docs.python.org/2/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##K6gsycjPM/r/v6AoM69EySM1JydfRyE8vygnRVHp/38A)
## [Python 2 (Cython)](http://cython.org/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##K6gsycjPM9JNBtP//xcUZeaVKHmk5uTk6yiE5xflpCgq/f8PAA)
## [Python 2 (IronPython)](http://ironpython.net/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##K6gsycjPM9LNLMrP@/@/oCgzr0TJIzUnJ19HITy/KCdFUen/fwA)
## [Python 2 (Jython)](http://www.jython.org/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##K6gsycjPM9LNAtP//xcUZeaVKHmk5uTk6yiE5xflpCgq/f8PAA)
## [Python 2 (PyPy)](http://pypy.org/), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##K6gsycjPM9ItqCyo/P@/oCgzr0TJIzUnJ19HITy/KCdFUen/fwA)
## [Python 3](https://docs.python.org/3/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##K6gsycjPM/7/v6AoM69EQ8kjNScnX0chPL8oJ0VRSfP/fwA)
## [Python 3 (Cython)](http://cython.org/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##K6gsycjPM9ZNBtP//xcUZeaVaCh5pObk5OsohOcX5aQoKmn@/w8A)
## [Python 3 (Stackless)](https://github.com/stackless-dev/stackless), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##K6gsycjPM9YtLklMzs5JLS7@/7@gKDOvREPJIzUnJ19HITy/KCdFUUnz/38A)
## [QuadR](https://github.com/abrudz/QuadRS), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##KyxNTCn6/98jNScnX0chPL8oJ0Xx/38A)
## [Quadrefunge-97 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##KyxNTClKTSvNS0/VtTTXzS1Jy/z/X0kxJacoP1xBJz8nJ9VDyc5KWSfe4f9/AA)
## [QuadS](https://github.com/abrudz/QuadRS), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##KyxNTCn@/98jNScnX0chPL8oJ0Xx/38A)
## [Quarterstaff](https://github.com/Destructible-Watermelon/Quarterstaff), 43 bytes
```
108>a72!101!a!a!a3!44!32!87!a3!a6!a!100!33!
```
[Try it online!](https://tio.run/##KyxNLCpJLSouSUxL@//f0MDCLtHcSNHQwFAxEQSNFU1MFI2NFC3MQexEM6CYoYGBorGx4v//AA)
## [Quintefunge-97 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##KyzNzCtJTSvNS0/VtTTXzS1Jy/z/X0kxJacoP1xBJz8nJ9VDyc5KWSfe4f9/AA)
## [R](https://www.r-project.org/), 20 bytes
```
cat("Hello, World!")
```
[Try it online!](https://tio.run/##K/r/PzmxREPJIzUnJ19HITy/KCdFUUnz/38A)
## [Racket](https://racket-lang.org/), 37 bytes
```
#lang racket
(display"Hello, World!")
```
[Try it online!](https://tio.run/##K0pMzk4t@f9fOScxL12hCMzj0kjJLC7ISaxU8kjNycnXUQjPL8pJUVTS/P8fAA)
## [Rail](https://esolangs.org/wiki/Rail), 27 bytes
```
$'main'
 -[Hello, World!]o#
```
[Try it online!](https://tio.run/##K0rMzPn/X0U9NzEzT51LQTfaIzUnJ19HITy/KCdFMTZf@f9/AA)
## [Random Brainfuck](https://github.com/TryItOnline/tio-transpilers), 76 bytes
```
+[+[<<<+>>>>]+<-<-<<<+<++]<<.<++.<++..+++.<<++.<---.>>.>.+++.------.>-.>>--.
```
[Try it online!](https://tio.run/##HYhRCoAwDEMPFNoThF5k7GNuCCJOGHj@2jUhvCSrzfE@cqx2zfPrtzsKCklYqIISjkWgkhrIKHbJJSJqppaXpNT2FXT/AQ)
## [Rapira](https://github.com/freeduke33/rerap2), 22 bytes
```
OUTPUT:"Hello, World!"
```
[Try it online!](https://tio.run/##K0osyCxK/P/fPzQkIDTESskjNScnX0chPL8oJ0VR6f9/AA)
## [Recursiva](https://github.com/officialaimm/recursiva), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##K0pNLi0qzixL/P9fySM1JydfRyE8vygnRfH/fwA)
## [Reason](https://reasonml.github.io/), 23 bytes
```
Js.log("Hello, World!")
```
[Try it online!](https://tio.run/##K0pNLM7P@//fq1gvJz9dQ8kjNScnX0chPL8oJ0VRSfP/fwA)
## [Red](http://www.red-lang.org/), 25 bytes
```
Red[]print"Hello, World!"
```
[Try it online!](https://tio.run/##K0pN@f8/KDUlOragKDOvRMkjNScnX0chPL8oJ0VR6f9/AA)
## [Reng](https://github.com/ConorOBrien-Foxx/Reng), 20 bytes
```
"Hello, World!"rao;~
```
[Try it online!](https://tio.run/##K0rNS///X8kjNScnX0chPL8oJ0VRqSgx37ru/38A)
## [ReRegex](https://github.com/TehFlaminTaco/ReRegex), 13 bytes
```
Hello, World!
```
[Try it online!](https://tio.run/##K0otSk1Prfj/3yM1JydfRyE8vygnRfH/fwA)
## [Reticular](https://github.com/ConorOBrien-Foxx/reticular), 17 bytes
```
"Hello, World!"p;
```
[Try it online!](https://tio.run/##K0otyUwuzUks@v9fySM1JydfRyE8vygnRVGpwPr/fwA)
## [Retina](https://github.com/m-ender/retina), 14 bytes
```

Hello, World!
```
[Try it online!](https://tio.run/##K0otycxL/P@fyyM1JydfRyE8vygnRfH/fwA)
## [Retina 0.8.2](https://github.com/m-ender/retina), 14 bytes
```

Hello, World!
```
[Try it online!](https://tio.run/##K0otycxL/P@fyyM1JydfRyE8vygnRfH/fwA)
## [Rexx (Regina)](http://www.rexx.org/), 18 bytes
```
say"Hello, World!"
```
[Try it online!](https://tio.run/##K0qtqPj/vzixUskjNScnX0chPL8oJ0VR6f9/AA)
## [rk](https://github.com/aaronryank/rk-lang), 37 bytes
```
rk:start
print: "Hello, World!"rk:end
```
[Try it online!](https://tio.run/##K8r@/78o26q4JLGohKugKDOvxEpBySM1JydfRyE8vygnRVEJKJ2al/L/PwA)
## [ROOP](https://github.com/alejandrocoria/ROOP), 17 bytes
```
"Hello, World!"
h
```
[Try it online!](https://tio.run/##K8rPL/j/X8kjNScnX0chPL8oJ0VRiSvj/38A)
## [Rotor](https://github.com/quartata/rotor-lang), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##K8ovyS/6/1/JIzUnJ19HITy/KCdF8f9/AA)
## [RProgN](https://github.com/TehFlaminTaco/Reverse-Programmer-Notation), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##Kyooyk/P@/9fySM1JydfRyE8vygnRfH/fwA)
## [RProgN 2](https://github.com/TehFlaminTaco/RProgN-2), 15 bytes
```
"Hello, World!"
```
[Try it online!](https://tio.run/##Kyooyk/P0zX6/1/JIzUnJ19HITy/KCdFUen/fwA)
## [Ruby](https://www.ruby-lang.org/), 19 bytes
```
puts'Hello, World!'
```
[Try it online!](https://tio.run/##KypNqvz/v6C0pFjdIzUnJ19HITy/KCdFUf3/fwA)
## [Rust](https://www.rust-lang.org/), 34 bytes
```
fn main(){print!("Hello, World!")}
```
[Try it online!](https://tio.run/##KyotLvn/Py1PITcxM09Ds7qgKDOvRFFDySM1JydfRyE8vygnRVFJs/b/fwA)
## [Röda](https://github.com/fergusq/roda), 23 bytes
```
main{["Hello, World!"]}
```
[Try it online!](https://tio.run/##K8pPSfz/PzcxM686WskjNScnX0chPL8oJ0VRKbb2/38A)
## [S.I.L.O.S](https://github.com/rjhunjhunwala/S.I.L.O.S), 19 bytes
```
print Hello, World!
```
[Try it online!](https://tio.run/##K87MyS/@/7@gKDOvRMEjNScnX0chPL8oJ0Xx/38A)
## [Sad-Flak](https://github.com/Destructible-Watermelon/Sad-Flak), 199 bytes
```
32
({}≤()≥)
(≤()≥)
99
({}≤()≥)
((<>[≤()≥]))
7
({}≤()≥)
((<>))≤()≥
5
({}≤()≥)
(≤()≥)
109
({}≤()≥)
(<>)(≤()≥)
85
({}≤()≥)
(≤()≥)
30
({}≤()≥)
(≤()≥)
42
({}≤()≥)
({≤()≥})(({()}))({()})(())
70
({}≤()≥)
≤≥
```
[Try it online!](https://tio.run/##K05M0U3LScz@/9/YiEujuvZR5xINzUedSzW5NBBMS0s0KQ0bu2gYN1ZTk8scU15TE8bnMsVpsKEBuslAjUjyFri1GhvglDJB90k1jF2rqaFRraFZq6kJoTQ0QI5HMwnIAtL////XdQQA)
## [Sakura](https://github.com/tuxcrafting/sakura), 1 byte
```
H
```
[Try it online!](https://tio.run/##K07MLi1K/P/f4/9/AA)
## [Scala](http://www.scala-lang.org/), 47 bytes
```
object Main extends App{print("Hello, World!")}
```
[Try it online!](https://tio.run/##K05OzEn8/z8/KSs1uUTBNzEzTyG1oiQ1L6VYwbGgoLqgKDOvREPJIzUnJ19HITy/KCdFUUmz9v9/AA)
## [sed](https://www.gnu.org/software/sed/), 14 bytes
```
cHello, World!
```
[Try it online!](https://tio.run/##K05N0U3PK/3/P9kjNScnX0chPL8oJ0Xx/38A)
## [sed 4.2.2](https://www.gnu.org/software/sed/), 19 bytes
```
cHello, World!
```
[Try it online!](https://tio.run/##K05N@f8/2SM1JydfRyE8vygnRfH/fwA)
## [Seed](https://github.com/TryItOnline/seed), 4203 bytes
```
20 854872453003476740699221564322673731945828554947586276010721089172712854441839676581917455319274850944955030258951339804246125714958815519550291630078076933441706558540342671975808828643360922071900333028778314875248417953197990571991784126564752005357199892690656368640420204822142316716413192024742766282266114842280731756458212469988291309261528542889299297601723286769284159107438930448971911102280330101196758384815655479640836157495863547199726234352265518586460633795171196315255736880028338460236768181141732764911402112878175632130129852788301009582463631290071329795384336617491655825493435803011947670180368458659271192428341035912236946048939139042310380278430049252171822721598175984923434205610723412240162418996808671543770639111617709604242882388664919702606792443015941265168129550718541372361144081848761690730764968771245566074501485020726368378675085908872608679630368472956274468410052703615106090238423979678950131481176272880569100533049143775921798055136871254424261001442543122666701145111965968366507060931708140304772342855064834334129143038575569044150428480231956133612367393837580345180691911525531699573096952433882387811884727975431823620782822755161559988205401134640722220804177812794328129589949692446031008866917615922944976151073653201316255518389496411696741029209242119521978920200314572718584995265523235225587228975886710511855501710470163649632761488899317729943053884132314641377747687975638119132094777769497069556255954031537245957811105217875011509899497752696062748928963281605780942517262774976217663461063680912331030221981433051827519906741285738915397005702326447635845195923640649166530310494885569783989508000344280715868581532826832242144647203531393142251025361866506821695860883605004105862208004440476654027574832078603305884731766236740069411566854496824754558761536201352147934963241039597221404341132342297870517293237489233057335406510464277610336142382379135365550299895416613763920950687921780736585299310706573253951966294045814905727514141733220565108490291792987304210662448111170752411153136765318541264632854767660676223663544921028492602135525959428999005153729028491208277493747933069008199074925710651071766675870081314909460661981433426167330215548196538791617762566403934129026219366764038390123622134753742930729751695349588862441999672547791630729398908283091638866715502470152431589429837867944760012419885615525232399584379209285060418518373512154801760060312646951597932345591416241634668119867158079946680321131213357200382937049485606706114467095019612014749723443159443363662563254359712162432143334612180576945072905749883870150120687696027984317320305291407322779803583395375616762530641605634303022155218169343410634115050596030685041633824154135240376022159918501703555881290333205131375705406831260759974112248490451605422031345264183102048614606636275942039438138959188478277971377232005036301145411215067576576667743288951344423152531417111852584846747428443123174595987315325304540564683047858415059703724263652136185848573853965992798725654430360647040362341567082462847275277303225817689141675391972818943419663764371222973269129542760661385278009266471167618553065823580448848795731295589715602705860758954890415040763604082216728159486423396295188510311881004469017351709060492844398219491990895826924575575549615118821417543037296628825303328056839433114519945243963946989899508355224823109677424196639930153649890175062456649384605721510239142861693109687536600667811037619175927995599388547421689316110236566026931360164495251160997857372500940728057700473763884480342708897319990346726967220426504612260565552531158509215849649565188655100774748485416791517853427613458459889062942881409801879085054494129489535044719193283409051007851153504224002807392992520076910314763705776345053922387355156981872691537772657428096384535960466923475731297217863371650154415835785630016335858514130863258775100537612371430357576913148500310344278511588325852376442503898849856566716198848377379400158332792027967216204970114516984638014129252882482309132898416484525230488700253065644547798869056136044415413099076332059572505138116227535024546891015836838323022822272664771489129085797354578016574544759934333471793
```
[Try it online!](https://tio.run/##JdfZdR05DATQVBwCSXDNZxyB8z@aWy3/WHpPTQK1Af3v79//fn5G@3PXvGfMVa3VPPvMtt8bo689a4x96lR/c91x15pvnnX3OLv1dkZv9/UzTvfdnLPfevvsdbtP51qeG2fe1d6cb61Wbaz7Vq96t80xdx/rdF/d29fq@ZPx@lbIue3sV@XM0/ZajlecYvpzf7uKUV3tptDmQ6WX0@85t7p21pjXoy8lnPeaa56afDa2vnzf2qrv0/vGfu7YtZ2prDbavPqfo7oL9@zpo415pr738N3e3S1zDGVWP04ET9eQ464WSl27r6Ayrgvg@QLZGaVwnQ2VrAfCWfdVm/M@tfTeW87USm@9w3LduhM4IJjnKe@Wc08g2@Uj9Z@xR81aqoLh9cXcbVdpvp8cUgpZ62jvNhCVE3cbpYzbrz76KX1Nt882OirPTUs1tNHHu2uce1NRc6sey4kD4qeXrkB8w8TGOO5QNagkBekjTURSrftlXyjtRRI@HYCp2VtBYSjmqQkIBbvXgnyr21w8iWG@sYZeAE9y66W8d33qFnStHSk6bIzZ@h5k@N4mEuStWYeAKtCq8LS3IzykjLp3p@t32gDYUZLLHP9ppANnRJCuXRTggnCOgI6QszvNnGrBbVMd7tfaG5@r9SieKkcUVUcZq931iNZHqQolHxrHBaw0p5@hC@cWdnsjawTRV8F3H5ZpPbLu/fh7xev55QlC0UF6BCu5@4K7FMRYM32CRj3Tbzgj21DR5@rRxVI53rSYC8lYb1zW5gmacXvbE0kVaHMLStbRJoKoF46QUCffbpZmZpqqV3oO9265kiSqjv546T0qxMDjTioMBaTWb5A4fK1Gn23Q3ZjMVThb6/NUEwC912SBM/xrAgSfSDpPTH1koR0b4XE3AmohmOmdISUSQedDlxNWjSC61aVKFvTcpBBgY2JwewQKJLp78E8mOHKuZB2LTa3Ebuwc4xG9om6iKaJr8IUe0vw8IU4ILojLkCgPAjbyFY5C7TOSwxM05xx@uUFjF2zYQS0YOUJDAwBFgAtfArGvSnCD9SY6YhLRByeJ@4FBF8KNuhPDQidF3L7F4XXqEBDCw5WQ8eze8KU@AmpcWTGhPOoMhy9dXZxInBaU6OMATgmqciAhjD0Vz/gzWc6eyIrDaKxCiOFxb/QjpF9ELY/oZCZFu2gArONQT5cj@COSNGRESQUIQRo7i9RudLtl7k4SYtooWJICCKZT1EGjwlxPgFK2/ivC2gnXFclVGo5kZ4Mq9vk3U4wrRP2aIZVeoseO5C5/62MxqaW9kxHRJFAPfWrT1mmB9Pn9wztXnZLTxov2t/nhyBav8DatH/y6YX2DL5BMYFGBwEJ7Ojzx9f00K4ijnNjVqWAQ8E8LTxWQm5lyIWh@kQ5BKeFaYs1UddC77AfW5qGZNJEnLaPSD4E4o7u@uMNklLKS3TvhuJPRmThSFwUJXzNE8awNCxQ@utB9FPm@P@hY@LQFC9AVkFky8jkJdNZIdScsZM6dfFnpIqMACr@qS4RJFTqUBGoWW1LjfWHOBxIcGV9ASXFSVeXJZxTWEkhIstSoaqJFdDBWNFPf0nGDg4rYXkKe8@0e4Q8Vijf08klihD5XNgDzQXYRq5bfb7i/iF7KglFQrSTW@IJBRhhf5wsTE8Hgga20ObW6bmRnz4PJquCNTaKKdkhP3H6TLI7cyYFvmNEBV/ugGc7A0psdJtFk6ajzGWyFrvbNKv9ncjzJbAjE5c5O9UqmQVCNjHm562KHudC5vkoMDOm9EjoriLTsHFx2g4Beo8wEi/TVYzYIUbEyJUhVdGcUCQKLHuhXKHQXCcyEj6bqN1lAZQXZWRdmgicu5GOTyffc2IKA5oybGRMiFmR50DZ3E7BuWVkflahukgeLG0/mhRiBLIVbkpw8shOaXSs18CvcQQ16nPRv6WPLSI9qTjRNWdazLuXwkciIniFVGZBZII3r@uZpTlc5HbPQJ@iTofTtunJofCtYxZc9o8EWrBTJczJDM5or@7JrODQRCCqHQspqkIGckRNkRG0SP5sF5JKDOSlBLA0M9Bc@aFnoBWLNkCzQsiHKNxPe/ja@eWvbkAa4Eh0mzic4Psk@ZETQtyekC7xpGHacI@Bf5mzW4Di0vtWwZdd1Tw/JmXuYswRm/xMyWZYy9r9lKkvuimiS0nhJ4HHat0xYpdRrv8LuTgkYsMrK0Cfi@IZ3MOb/nmwXJj1GIvE46304PgPhZaXj3uyq2QWysZy8uGT2e3qEhRV0yDrb/A3apJOl6obx@jYkRovVBT7HyQMBZ2Al8Mgo@@kLyeMXJLncMipmgsPxBu5MNr1v117ZWikMuPjO6vg9blSzoADYGd9Rdl6bsh@7CpeCZ0UhVlEP7LwboN0TIwcAy6uJGDMTCZrEowPc4yM7UtwrU825kwhDRV6gKAAJlczzK5yz8rACSeFgZ0fM1FifXAWORULtN@vRyzSRhTYmu3@0G@lFNZYAM2rl@B1Lmf@yAi8jgyFLpTTodGANbhkhiWvEewHDZN57pJ5FE5Xf2Zju33dZ6Nv3jvW9QuWl7WTx5SRNnXQoM5zp@yyT2KEvgyObdlYTa5PG4jJ448KpeQGwFo5MhU@WJwM270teXpCY1RbNish7aOIHCjdTtezurGnbX9/ufbLxnm8vXjH@@3b0lUXx22p@@xCaI6M7RrJxiWrY0MkKle7M0LCbMKNJ4sKE5sjQGFn9E8ote9@nSa2Zy7AMgOCg3WixZUt0LC5w8k0fYZaJ@mWuFJnfdEPey9tSfDZ/I7VlHO8vOLlUeQKLGHe278rEWzPZ8JXFHXpJbvOo15CYXvs3mYBZyWg/yGbZAzkgE7z1jRNT/tXPz/8)
## [Self-modifying Brainfuck](https://soulsphere.org/hacks/smbf/), 19 bytes
```
<[.<] !dlroW ,olleH
```
[Try it online!](https://tio.run/##K85NSvv/3yZazyaWQTElpyg/XEEnPycn1eP/fwA)
## [Septefunge-97 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##K04tKElNK81LT9W1NNfNLUnL/P9fSTElpyg/XEEnPycn1UPJzkpZJ97h/38A)
## [Seriously](https://github.com/Mego/Seriously/tree/v1), 1 byte
```
H
```
[Try it online!](https://tio.run/##K04tyswvLc6p/P/f4/9/AA)
## [Sesos](https://github.com/DennisMitchell/sesos), 21 bytes
```
add 72
put
fwd 1
add 101
put
add 7
put
put
add 3
put
fwd 1
add 44
put
sub 12
put
rwd 2
add 15
put
fwd 1
put
add 3
put
sub 6
put
sub 8
put
fwd 1
add 1
put
```
[Try it online!](https://tio.run/##K04tzi/@/z8xJUXB3IiroLSEK608RcGQCyRgaGAIFgFLglkwnjGaShMTsEBxaZKCIcSUIqCcEcQUUyTFqAaA1JvBWRbo1oP4//8DAA)
## [Set](https://github.com/somebody1234/Set), 84 bytes
```
set!Hset!101set!108set!108set!111set!44set!32set!Wset!111set!114set!108set!100set!33
```
[Try it online!](https://tio.run/##K04t@f@/OLVE0QNEGBoYQigLZMoQLGhiAiKNjUBkOJK4oaEJih4DsDLj//8B)
## [Sexefunge-97 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##K06tSE0rzUtP1bU0180tScv8/19JMSWnKD9cQSc/JyfVQ8nOSlkn3uH/fwA)
## [Shakespeare Programming Language](https://github.com/TryItOnline/spl), 612 bytes
```
,.Ajax,.Puck,.Act I:.Scene I:.[Enter Ajax and Puck]Ajax:You big big big cat!Puck:You is the sum of I the square of I!Speak thy!You is the square of the sum of I a big cat!Remember the sum of twice twice I a cat!Remember you!Remember the sum of I you!You is the sum of you a cat!Speak thy!Recall!Speak thy!Speak thy!Remember you!Ajax:You is the sum of a big cat a cat!Puck:You is the sum of you I!Speak thy!Remember the sum of you I!Remember you!You is twice twice the sum of a big big big cat I!Remember the sum of twice you a pig!Remember a big big big big big cat!Scene V:.Puck:Speak thy!Recall!Let us Scene V!
```
[Try it online!](https://tio.run/##dVLLDoIwEPyV5U74AG4ePDTxYCAxMcZDqSsiT6GN8vVIAcs2xUOb7s7s7HbarimGwQ92T/7xg6MS@XgWElgYxAIr1IfLvpLYgqYAr26gWVcdhedaQZKlZgkuPY1OQNaBfCB0qoT6DmwOXoq3OMVe3CDPx2zvUbYhWLXcyEdYYpmM4xBcvjOBy665Fq@v1WYRmxB30DG7SKwDRih4UZAEhUgfY4otaaZfhP9YpDuzLWmHYzX9CRETnN7kgWi54@F8@SZLV44tQF96/iCncPo2oePWASWoDhaWNwxf)
## [ShapeScript](https://github.com/DennisMitchell/shapescript), 15 bytes
```
'Hello, World!'
```
[Try it online!](https://tio.run/##K85ILEgtTi7KLCj5/1/dIzUnJ19HITy/KCdFUf3/fwA)
## [shortC](https://github.com/aaronryank/shortC), 16 bytes
```
AR"Hello, World!
```
[Try it online!](https://tio.run/##K87ILypJ/v/fMUjJIzUnJ19HITy/KCdF8f9/AA)
## [Shove](https://github.com/TryItOnline/shove), 16 bytes
```
"Hello, World!"S
```
[Try it online!](https://tio.run/##K87IL0v9/1/JIzUnJ19HITy/KCdFUSn4/38A)
## [Shtriped](https://github.com/HelkaHomba/shtriped), 239 bytes
```
e n
e b
i b
+ x y
 +
  i x
  d y
  +
 +
 d x
0
 + b b b
1
 + b n n
 0
z x
 d x
 z x
D
 1
 s n
 z n n
 z b b
 i b
Y
 0
 0
Z
 1
 Y
 Y
B
 0
 1
1
Z
1
Y
1
Y
D
B
B
1
0
Z
Y
D
B
1
Y
B
0
Z
D
1
B
B
Y
1
0
D
Y
1
1
Y
B
Z
D
B
Y
1
0
Z
Y
D
B
1
1
1
1
B
0
D
```
[Try it online!](https://tio.run/##XU05DsQgDOz9iunTJF9AfALKCKSliaLNFgmfJzOmW9mG8RxwfX7fdtYyRsVhFbs1zoIbj2ExoOHmWbRqZxcyKxF2lW0THoxjtS67HBCKBsqXpD4d3TPQJ0l@dnZTUgenNr6ZOcknkg1EMs5NbPA9EktNrke/p5rdmf5ys5SNY7w)
## [Shnap](https://github.com/ShnapLang/Shnap), 22 bytes
```
print("Hello, World!")
```
[Try it online!}(https://tio.run/##K87ISyz4/7@gKDOvREPJIzUnJ19HITy/KCdFUUnz/38A)
## [Sidef](https://github.com/trizen/sidef), 18 bytes
```
say"Hello, World!"
```
[Try it online!](https://tio.run/##K85MSU37/784sVLJIzUnJ19HITy/KCdFUen/fwA)
## [Simplefunge](https://github.com/TryItOnline/simplefunge), 57 bytes
```
89*O5!+!*1+O7+OO3+O&47*&-O34*&-O9!*6+O`&O3+O6&-O8&-O`1+O@
```
[Try it online!](https://tio.run/##K87MLchJTSvNS0/9/9/CUsvfVFFbUctQ299c29/fWNtfzcRcS03X39gERFoqaplp@yeogSTMgHwLIE4AqnX4/x8A)
## [Simula (cim)](https://directory.fsf.org/wiki/Cim), 24 bytes
```
OutText("Hello, World!")
```
[Try it online!](https://tio.run/##K87MLc1J/P/fv7QkJLWiREPJIzUnJ19HITy/KCdFUUnz/38A)
## [SISAL](https://github.com/TryItOnline/sisalc), INVALID
## [Snails](https://github.com/feresum/PMA), INVALID
## [SNOBOL4 (CSNOBOL4)](http://www.snobol4.org/csnobol4/), 28 bytes
```
 OUTPUT ='Hello, World!'
END
```
[Try it online!](https://tio.run/##K87LT8rPMfn/X8E/NCQgNETBVt0jNScnX0chPL8oJ0VRncvVz@X/fwA)
## [Snowman](http://github.com/KeyboardFire/snowman-lang), 18 bytes
```
("Hello, World!"sP
```
[Try it online!](https://tio.run/##K87LL89NzPv/X0PJIzUnJ19HITy/KCdFUak44P9/AA)
## [SNUSP (Modular)](https://github.com/TryItOnline/snusp), 291 bytes
```
      /@@@@++++#               #+++@@\                #-----@@@\n
$@\H.@/e.+++++++l.l.+++o.>>++++.< .<@/w.@\o.+++r.++@\l.@\d.>+.@/.#
  \@@@@=>++++>+++++<<@+++++#       #---@@/!=========/!==/
```
[Try it online!](https://tio.run/##nc5BCgIxDAXQ/ZwiUnfFnwt0yl96iCx1VxxxEI9fk8osRETwLcpPaclfL/f12rsMSpddknfJ70ib9rQjqGfkl4YWcUGtMaIICvXww2P7/hVtiTc3RGygnVCzL0aaRCxazmPhOHIpo/RH638l70jqbt5E1N6f)
## [SNUSP (Snuspi)](https://github.com/graue/esofiles/tree/master/snusp), 45 bytes
```
72+.29+.7+..3+.67-.12-.55+.24+.3+.6-.8-.67-.#
```
[Try it online!](https://tio.run/##K84rLS7I/P/f3Ehbz8hSW89cW0/PWFvPzFxXz9BIV8/UFChsog0W0tWz0AVLKP//DwA)
## [Somme](https://github.com/ConorOBrien-Foxx/Somme), 38 bytes
```
8s+vi:7+::J:^B4*25p9s6+v:J:6-:8-25pim,
```
[Try it online!](https://tio.run/##K87PzU39/9@iWLss08pc28rKyyrOyUTLyLTAsthMuwzINdO1stAF8jNzdf7/BwA)
## [Spaced](https://github.com/ConorOBrien-Foxx/spaced), 67 bytes
```
[,a,,b,,c,,d,,e,f,g,,h,,i,,j]='Helo,Wrd!';a+b+c+c+d+e+f+g+d+h+c+i+j
```
[Try it online!](https://tio.run/##Dcc7CoAwEADRs1il2LmB2HsDC7GI2c0PQdH7s4YpHvM9MZm670Q4IYGCkSlQoUE/lrDadbO9OoU5yilppGKSpQzruCbd/Qc)
## [SQLite](https://www.sqlite.org/), 21 bytes
```
select'Hello, World!'
```
[Try it online!](https://tio.run/##Ky7MySxJ/f@/ODUnNblE3SM1JydfRyE8vygnRVH9/38A)
## [Squirrel](http://www.squirrel-lang.org/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##Ky4szSwqSs35/7@gKDOvREPJIzUnJ19HITy/KCdFUUnz/38A)
## [Stack Cats](https://github.com/m-ender/stackcats), 134 bytes
```
-*(:^-_-_:-_:-_:-_:-_-_:[:^]]:^!-*!->[!_>[!_>[{]>[^-_-_:]]<<<}>[!-:^[[\\>]:^[[>:[>:^[<<]]\\>[*>+:^:-_]:^[[-_*[>>>[-_[/<]>+^[>[<<]]*>[)
```
[Try it online!](https://tio.run/##TU4xCsNADHvLba2D6W6MPqLYR8jYbskW8varmywFWQJJCG/7sr7XZd/GUHlYatdufyiiZYRlU2kKtn7fEeDdjnD3s1y1JOcZ8VNYIekeURYFk2XtXZl2IYBSvjwwJXEVBXyOeuTzBQ)
## [Stacked](https://github.com/ConorOBrien-Foxx/stacked), 18 bytes
```
'Hello, World!'out
```
[Try it online!](https://tio.run/##Ky5JTM5OTfn/X90jNScnX0chPL8oJ0VRPb@05P9/AA)
## [Standard ML (MLton)](http://www.mlton.org/), 21 bytes
```
print"Hello, World!";
```
[Try it online!](https://tio.run/##K87N0c3NKcnP@/@/oCgzr0TJIzUnJ19HITy/KCdFUcn6/38A)
## [Starry](https://esolangs.org/wiki/Starry), 169 bytes
```
        + + +* +  * + + +* + .* +         + +* * +      +* .  + + . + . +        + +   +* + . +          +   * +* + .         + +  * +* . +*      + * . + .* . . .  + * .
```
[Try it online!](https://tio.run/##VU3JDQAgCFuFd03YyRXQj9MjCF4QoGna0noVGaqUVbxhi3AxL@IqQIcwzOHinCeI0v64F8TmPzEizFZyiEw/HF8Mqk4)
## [Stax](https://github.com/tomtheisen/stax), 8 bytes
```
èï┬▀↨╩4G
```
[Try it online!](https://tio.run/##ARoA5f9zdGF4///DqMOv4pSs4paA4oao4pWpNEf//w)
## [Stencil](https://github.com/abrudz/Stencil), 1 byte
```
S
```
[Try it online!](https://tio.run/##Ky5JzUvOzPn/P/j/f4/UnJx8HYXw/KKcFEUA)
## [Stones](https://github.com/cheezgi/stones), 647 bytes
```
red down three
red up three
yellow up
blue left
red down two
green down
yellow down
green down
yellow up
green down
green down
red down one
yellow down
blue left
red up three
yellow down
green down
green down
green down
blue left
blue left
red right one
yellow down
blue left
red up three
red up two
yellow up
green down
green down
red left two
red left two
yellow down
yellow down
blue left
blue left
red down three
red down three
yellow up
red left two
yellow down
blue left
blue right
green down
red right one
yellow down
green down
blue left
red right one
yellow down
blue left
blue left
red down one
yellow down
blue right
blue left
blue left
```
[Try it online!](https://tio.run/##jZBLDoAgDET3nIKzGSqYEDCAIZ4eK374WBN2HTK8mdYHa8Cn5EBwYaPhQTkAdsptvcUOWtuImk16A65hDqz4o2USXSbLx5vn7zMiqsdqfHHYpmG0iX2lHkOPhdHS3CJVGE18BK47sswJyOZG1Dl0JnXhN7@SpcNvQAfN2/Y16ROQtxu5GNGeNF9diH8pHQ)
## [str](https://github.com/ConorOBrien-Foxx/str), 17 bytes
```
`Hello, World!`o;
```
[Try it online!](https://tio.run/##Ky4p@v8/wSM1JydfRyE8vygnRTEh3/r/fwA)
## [Straw](https://github.com/tuxcrafting/straw), 2 bytes
```
->
```
[Try it online!](https://tio.run/##Ky4pSiz//1/X7v9/AA)
## [Subskin](https://github.com/TryItOnline/subskin), 47 bytes
```

48
6f
2
a
1
4
1
4


a
3
3

43
4f
18

-3
3
b
4e
```
[Try it online!](https://tio.run/##Ky5NKs7OzPv/n8vEgsssjcuIK5HLkMsEjLmAbGMg5DIx5jJJ4zK04OLSBfGTuExS//8HAA)
## [Surface](https://github.com/TryItOnline/surface), 516 bytes
```
++++++++(-v        .     o]v    
   -      e++++v   !     ^ v    
   -           e+++++++++^ x    
   -     e+++++++++o   v-(e.    
   -     e+++++++++o   +  ^o    
   -               +v]ev        
   e----------o    +- ^+        
   e----------o    +- ^o        
+++.v              +e-.+++++++..
-.^!+              +e-----------
  oo+              +.e+.@       
.--o+              .+v .--------
   -+              ++           
   -+              ++           
   -+              ++           
   -+              .+
```
[Try it online!](https://tio.run/##tZBBCgIxDEX3c4rObiDkn8GLTEEkbgOKxdvXNNZ2poqu/NBC0te80uvtcj6eJGeqWTiFGviuqzcmW/zsS@FKc/YyhhHolCeG@x7oR2pV4kXwDSBz6CdFCaVV2osLINzil4hDpF@ANsCcSINCGPU5wMSIM70BPaZQHQEI4fBSwMQDAPtPbCYEHids6/8AoJwf)
## [Swap](https://github.com/splcurran/Swap), 29 bytes
```
"!dlroW ,olleH"ooooooooooooox
```
[Try it online!](https://tio.run/##Ky5PLPj/X0kxJacoP1xBJz8nJ9VDKR8ZVPz/DwA)
## [Swift 4](https://developer.apple.com/swift/), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##Ky7PTCsx@f@/oCgzr0RDySM1JydfRyE8vygnRVFJ8/9/AA)
## [Symbolic Brainfuck](https://github.com/KelsonBall/Esolangs.Sbf), 182 bytes
```
▲²²²▲²²²¡½½½▲▲▲²▲²²▲¡½▲▲▲▲²¡¡▲▲▲¡α▲²²▲²▲²²¡ß▲²²²²²¡ß²▼¡α¡▲▲▲¡½▼▼▼²¡½½▼▼²²¡ß▲¡
```
[Try it online!](https://tio.run/##K05K@///0bRNh8AQzji08NBeEAQKQBBcDkQtRJKACC88tBDBXXhuI5JiuKELD89HmA8VAMnuAWlA0Q8yfg8EwZwC58HNWfj/PwA)
## [Symbolic Python](https://github.com/FTcode/Symbolic-Python), 200 bytes
```
__=-~(_==_)
__=`_`[~__]+`_>_`[__::__]+`''`[-__::~__**__]
_=_==_
___='%'+__[-_]
__,_=___+__[-~_]+__[_]*-~_+__[_>_]+', '+___+__[_>_]+`_`[_]+__[-~_-_]+__[~_]+'!',-~-~_
___=_*_<<_
_=__%(___,___+_*-~-~_)
```
[Try it online!](https://tio.run/##RU1LDoIwEN1zCl2QgdJegDBchJDX4EYTFRPdsOkNvJQXK2/KwtW877z39ljW@@0SXtvnuj5zBjSkBqpoK@KIOCVg7iJGQqDvC5PfV@IUjNN2jmIFtRpbUKmlA@hThacBFJ7Y5cXsCAsaqYg/Wfwv2OqRZCwcyKpyFh8StTICh2GAzaJuYDv2wpVAm/MO)
## [Syms](https://github.com/CatsAreFluffy/syms), 16 bytes
```
{Hello, World!}>
```
[Try it online!](https://tio.run/##K67MLf7/v9ojNScnX0chPL8oJ0Wx1u7/fwA)
## [TacO](https://github.com/TehFlaminTaco/TacO), 16 bytes
```
@"Hello, World!"
```
[Try it online!](https://tio.run/##K0lMzv//30HJIzUnJ19HITy/KCdFUen/fwA)
## [Tampio (functional)](https://github.com/fergusq/tampio/tree/functional), INVALID
## [Tampio (imperative)](https://github.com/fergusq/tampio), 46 bytes
```
Kun aloitetaan,tulostetaan tie"Hello, World!".
```
[Try it online!](https://tio.run/##K0nMLcjMz/z/37s0TyExJz@zJLUkMTFPp6Q0J78YwlYoyUxV8kjNycnXUQjPL8pJUVTS@/8fAA)
## [Taxi](https://bigzaphod.github.io/Taxi/), 183 bytes
```
"Hello, World!"is waiting at Writer's Depot.Go to Writer's Depot:w 1 r 3 l 2 l.Pickup a passenger going to Post Office.Go to Post Office:e 1 r 2 r 1 l.Go to Taxi Garage:n 1 r 1 l 1 r.
```
[Try it online!](https://tio.run/##XY6xCsJAEER/ZUxjI4HELrUQO1MIqZe4ORaPbLjbEP/@vEQLsRgW5rGPMXpJSsWVvdcTeg3@cSgkYiUxmRzI0AcxDseIC89qZasw/SubFRUCzvCo4ctOhucygzBTjDw5DnC62fJjp9FwG0cZ@Kv6aRrePXVOlT0ffs8T0VIgx82088y2W6b0Bg)
## [Tcl](http://tcl.tk/), 19 bytes
```
puts Hello,\ World!
```
[Try it online!](https://tio.run/##K0nO@f@/oLSkWMEjNScnXydGITy/KCdF8f9/AA)
## [tcsh](http://www.tcsh.org/), 18 bytes
```
echo Hello, World!
```
[Try it online!](https://tio.run/##K0kuzvj/PzU5I1/BIzUnJ19HITy/KCdF8f9/AA)
## [TemplAt](https://github.com/ConorOBrien-Foxx/attache/blob/master/TemplAt.md), 37 bytes
```
<attache>Print["Hello, World!"]Exit[]
```
[Try it online!](https://tio.run/##K0nNLchJLPn/3yaxpCQxOSPVLqAoM68kWskjNScnX0chPL8oJ0VRKda1IrMkOvb/fwA)
## [Templates Considered Harmful](https://github.com/feresum/tmp-lang), 50 bytes
```
St<72,'e','l','l','o',44,32,87,'o','r','l','d',33>
```
[Try it online!](https://tio.run/##K0nNLchJLEkt/v8/uMTG3EhHPVVdRz0HivPVdUxMdIyNdCzMwRz1IqhEirqOsbHd//8A)
## [Threead](https://github.com/TehFlaminTaco/Threead), 16 bytes
```
"Hello, World!"o
```
[Try it online!](https://tio.run/##K8koSk1NTPn/X8kjNScnX0chPL8oJ0VRKf//fwA)
## [Thue](https://esolangs.org/wiki/Thue), 25 bytes
```
a::=~Hello, World!
::=
a

```
[Try it online!](https://tio.run/##K8koTf3/P9HKyrbOIzUnJ19HITy/KCdFkQsowpXI9f8/AA)
## [Thutu](https://esolangs.org/wiki/Thutu), 20 bytes
```
/=1/Hello, World!=x/
```
[Try it online!](https://tio.run/##K8koLSn9/1/f1lDfIzUnJ19HITy/KCdF0bZC//9/AA)
## [TinCan](https://github.com/TryItOnline/tincan), 532 bytes
```
#  -72, Z, -1                          #
# -101, Y, -1                          #
# -108, X, -1                          #
# -108, W, -1                          #
# -111, V, -1                          #
#  -44, U, -1                          #
#  -32, T, -1                          #
#  -87, S, -1                          #
# -111, R, -1                          #
# -114, Q, -1                          #
# -108, P, -1                          #
# -100, O, -1                          #
#  -33, N, -1                          #
```
[Try it online!](https://tio.run/##jdA7CsAgEATQPqcYsF1Bo6CnyP/fhVRprHJ/4wVCZtt9sDP73Ok6U84K0KEWHAJt8TmqUmVvrGCnYBRsLFwZaMvp5R9Cey@YGehK64mBMQhGNuNAwZKxZ9/TUdAIWqq1EzQ/MOcX)
## [tinyBF](https://github.com/TryItOnline/brainfuck), 105 bytes
```
=++>+>>=+|+|=>+=>+++>+>+>+=>>>|=>=|>>++==>=++++++===>>+====>>==>=+==>>==>>===>>>===+++==>>==>>=+==>>>=+==
```
[Try it online!](https://tio.run/##LYqxDcBADAIHYgYYJkWkNKnSRPLufsy/heB08ve8/3V3ExAkolAUnAgMSlYs2dGAHI2a9sQeUMx0no7Dlp7uBQ)
## [tinylisp](https://github.com/dloscutoff/Esolangs/tree/master/tinylisp), 41 bytes
```
(load library)(join(q(Hello, World!))spc)
```
[Try it online!](https://tio.run/##K8nMq8zJLC74/18jJz8xRSEnM6kosahSUyMrPzNPo1DDIzUnJ19HITy/KCdFUVOzuCBZ8/9/AA)
## [TIS](https://github.com/Phlarx/tis.git), 170 bytes
```
@0
MOV 72 DOWN
MOV 101 DOWN
MOV 108 DOWN
MOV 108 DOWN
MOV 111 DOWN
MOV 44 DOWN
MOV 32 DOWN
MOV 87 DOWN
MOV 111 DOWN
MOV 114 DOWN
MOV 108 DOWN
MOV 100 DOWN
MOV 33 DOWN
HCF
```
[Try it online!](https://tio.run/##K8ks/v/fwYDL1z9MwdxIwcU/3A/MNjQwROZY4OIYIikzMUGwjZHMsjDHocHQ0ASnJQZIZhlD2B7Obv///zf8bwgA)
## [TRANSCRIPT](https://web.archive.org/web/20071018030927/http://www.corknut.org/code/transcript/), 36 bytes
```
He is here.
>HE, Hello, World!
>X HE
```
[Try it online!](https://tio.run/##KylKzCtOLsosKPn/3yNVIbNYISO1KFWPy87DVUfBIzUnJ19HITy/KCdFkcsuQsHD9f9/AA)
## [Trefunge-97 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##KylKTSvNS0/VtTTXzS1Jy/z/X0kxJacoP1xBJz8nJ9VDyc5KWSfe4f9/AA)
## [Trefunge-98 (PyFunge)](https://pythonhosted.org/PyFunge/), 19 bytes
```
"!dlroW ,olleH"ck,@
```
[Try it online!](https://tio.run/##KylKTSvNS0/VtbTQLagEM///V1JMySnKD1fQyc/JSfVQSs7Wcfj/HwA)
## [Triangular](https://github.com/aaronryank/triangular), 66 bytes
```
8.9,*<>@5\,1*6<>-+@7\,+3@@+<>@:3_7+\,3@-*43@<>*9-@p@3+\@_3@-8@-6@<
```
[Try it online!](https://tio.run/##DchLCoAgFAXQ/bxPEK/8hMhdiCCOIogIqfVbZ3iefrRrf8/WxwhTFEoZa5GZXMrK8EXYAP53s@q5iEFpMaRMUXHDuKD@F6AOaYwP)
## [Triangularity](https://github.com/Mr-Xcoder/Triangularity), 49 bytes
```
.... ....
..."!"...
.."rld"..
."o, Wo".
"Hell"+++
```
[Try it online!](https://tio.run/##KynKTMxLL81JLMosqfz/Xw8IFEAEFxArKSpBWEpFOSlKIJZSvo5CeL6SHpeSR2pOjpK2tvb//wA)
## [Trigger](http://yiap.nfshost.com/esoteric/trigger/trigger.html), 40 bytes
```
HHHeeelll lllooo,,,   WWWooorrrlllddd!!!
```
[Try it online!](https://tio.run/##KynKTE9PLfr/38PDIzU1NScnRwGI8/PzdXR0FBQUwsPDgeyioiKgYEpKiqKi4v//AA)
## [TrumpScript](https://github.com/samshadwell/TrumpScript), 36 bytes
```
say "Hello, World!"America is great.
```
[Try it online!](https://tio.run/##KykqzS0oTi7KLCj5/784sVJBySM1JydfRyE8vygnRVHJMTe1KDM5USGzWCG9KDWxRO//fwA)
## [Turtlèd](https://github.com/Destructible-Watermelon/Turtl-d), 14 bytes
```
"Hello, World!
```
[Try it online!](https://tio.run/##KyktKslJTfn/X8kjNScnX0chPL8oJ0Xx/38A)
## [TypeScript](https://www.typescriptlang.org), 28 bytes
```
console.log('Hello, World!')
```
[Try it online!](https://tio.run/##K6ksSC1OLsosKPn/Pzk/rzg/J1UvJz9dQ90jNScnX0chPL8oJ0VRXfP/fwA)
## [uBASIC](https://github.com/EtchedPixels/ubasic), 17 bytes
```
0?"Hello, World!"
```
[Try it online!](https://tio.run/##K01KLM5M/v/fwF7JIzUnJ19HITy/KCdFUen/fwA)
## [Underload](https://github.com/catseye/stringie), 16 bytes
```
(Hello, World!)S
```
[Try it online!](https://tio.run/##K81LSS3KyU9M@f9fwyM1JydfRyE8vygnRVEz@P9/AA)
## [Unefunge-97 (MTFI)](https://github.com/TryItOnline/befunge-97-mtfi), 21 bytes
```
"!dlroW ,olleH">:#,_@
```
[Try it online!](https://tio.run/##K81LTSvNS0/VtTTXzS1Jy/z/X0kxJacoP1xBJz8nJ9VDyc5KWSfe4f9/AA)
## [Unefunge-98 (PyFunge)](https://pythonhosted.org/PyFunge/), 19 bytes
```
"!dlroW ,olleH"ck,@
```
[Try it online!](https://tio.run/##K81LTSvNS0/VtbTQLagEM///V1JMySnKD1fQyc/JSfVQSs7Wcfj/HwA)
## [Unicat](https://github.com/gemdude46/unicat), 832 bytes
```
😻😹😸🙀🙀😹😹😸🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😼😽🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😽😼🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😽😼🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😽😿🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😽😼🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😼😸🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😺😿🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😽😿🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😾😺🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😽😼🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😼😼🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😼😹🙀🙀😽😼😸🙀🙀😻😹😸🙀🙀😹😺🙀🙀😽😼😸🙀🙀🙀🙀
```
[Try it online!](https://tio.run/##K83LTE4s@f//w/wZu4F4JxDv@DB/ZgMEg/noYnuBeA@aGC69eyDqydILVTsgeveToZdcO/dQEL67yHQrJf4E8fdB7KZ73OyhIIx3kh/G@PRB8P//AA)
## [Unlambda](http://www.madore.org/~david/programs/unlambda/), 36 bytes
```
`.!`.d`.l`.r``.W`. `.,``.l`c`.H.e.oi
```
[Try it online!](https://tio.run/##K83LScxNSkn8/z9BTzFBLyVBLydBryghQS88QU8hQU8nASSQnKDnoZeql5/5/z8A)
## [Unreadable](https://esolangs.org/wiki/Unreadable), 577 bytes
```
'"'""'""'""'"'"'""""""'""'"""'""'""'""'""'""'""'""'"'""'""""""'""'""'""'"""'""'""'""'""'""'""'""'""'""'""'""'""'""'""""""'""'""'"""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'"'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""""""'""""""""'"""'""'""'""'""'""'""'""'""'""'""'""'""'""""""'"""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'""'"""'"'"""""""'""""""""'"""'"'"""""""'"""'"'"""""""'""'""'"""'"'""'""'""'"'""'""'""'"""""""'""'"""'"'"""""""'""'"""'"'"""""""'""'""'""'"""'"'""'"""""""'"""
```
[Try it online!](https://tio.run/##K80rSk1MSUzKSf3/X11JXQmOwBwQgAggS6EqQ1WHXzUWhKKVBH1ItlMdQd2EYJCoT53GCBE56M5Ux8VD1ogt9FCjmoAAmmFwG///BwA)
## [V](https://github.com/DJMcMayhem/V), 14 bytes
```
iHello, World!
```
[Try it online!](https://tio.run/##K/v/P9MjNScnX0chPL8oJ0Xx/38A)
## [Vala](https://wiki.gnome.org/Projects/Vala), 36 bytes
```
void main(){print("Hello, World!");}
```
[Try it online!](https://tio.run/##K0vMSfz/vyw/M0UhNzEzT0OzuqAoM69EQ8kjNScnX0chPL8oJ0VRSdO69v9/AA)
## [VAR](https://github.com/machalvan/VAR/), 19 bytes
```
OUT "Hello, World!"
```
[Try it online!](https://tio.run/##K0ss@v/fPzREQckjNScnX0chPL8oJ0VR6f9/AA)
## [Verbosity](https://github.com/cairdcoinheringaahing/Verbosity), 390 bytes
```
Include<Integer>
Include<MetaFunctions>
Include<Output>
Include<String>
Integer:DefineVariable<o; 1>
Output:DefineVariable<P; 0>
String:DefineVariable<s; "Hello, World!">
String:RedefineVariable<s; String:RemoveCharactersFromStart<s; o>>
String:RedefineVariable<s; String:TakeFirstCharacters<s; o>>
Output:DisplayAsText<P; s>
DefineMain<> [
MetaFunctions:ExecuteScript<MetaFunctions@FILE>
]
```
[Try it online!](https://tio.run/##jVA9T8MwEN39K0xnBlibyAJBo0aiApEKBsRwdY72hGtH53PV/vpAiNKo7cJ470v33g55FSLJoW1Lb12qMS@94BrZqAFYoECRvBUKPo7wc5ImyXhXwuTX3f3nnz7iF3l8AyZYOcxDpm@N6k3n3Eumb4zqA865mOnJHJ0L1/o9sKuvJkflK9YX2iO1DTt82ACDFeRYcNhWAiydJpj/RCzhGwviKGPKYB5aUGwcHO7jEvfSlfhdp/9@AeRzoz/UyXbT2R5tEqwsUyOnu94V5dPMqM@2/QE)
## [Visual Basic .NET (.NET Core)](https://www.microsoft.com/net/core/platform), 67 bytes
```
Module H
Sub Main
Console.Write("Hello, World!")
End Sub
End Module
```
[Try it online!](https://tio.run/##K0vSTc4vSv3/3zc/pTQnVcGDK7g0ScE3MTOPyzk/rzg/J1UvvCizJFVDySM1JydfRyE8vygnRVFJk8s1L0UBqBZMQzT//w8A)
## [Visual Basic .NET (Mono)](http://www.mono-project.com/docs/about-mono/languages/visualbasic/), 67 bytes
```
Module H
Sub Main
Console.Write("Hello, World!")
End Sub
End Module
```
[Try it online!](https://tio.run/##K8ssLk3M0U1KLM5M1s1LLdHNzc/L///fNz@lNCdVwYMruDRJwTcxM4/LOT@vOD8nVS@8KLMkVUPJIzUnJ19HITy/KCdFUUmTyzUvRQGoFkxDNP//DwA)
## [Vitsy](https://github.com/VTCAKAVSMoACE/Vitsy), 16 bytes
```
"!dlroW ,olleH"Z
```
[Try it online!](https://tio.run/##K8ssKa78/19JMSWnKD9cQSc/JyfVQynq/38A)
## [VSL](https://github.com/vsl-lang/VSL), 32 bytes
```
fn main(){puts(`Hello, World!`)}
```
[Try it online!](https://tio.run/##KyvO@f8/LU8hNzEzT0OzuqC0pFgjwSM1JydfRyE8vygnRTFBs/b/fwA)
## [Whirl](https://bigzaphod.github.io/Whirl/), 955 bytes
```
1100001110010001111100110000000000000100000100000100000110000010000100100110011111100010011111001100000000000000000100000100000100000110001111100010001111100100100110011111100011100111110000000000000000000000000001001001100000011111100011100111110000000000010010011001111110001001111100110000000000000000010000010001111100000111110001000001000001000001000001001001100111111000100111110011000001000001000001000001000001000001000001000001000001001001100111111000100111110011000000000000000000000000010000010000000001000001000001000001000111110000011111000000000001001001100111111000100111110011000000000100000100000000010000010000000000011111000001111100010000010000000001001001100111111000111001111100000000000100100111001111110001111001111100000000000000000000000111100000111001000111001111110001111001111100000000000000000000000000000001111000001110010001100111111000100111110011000001000001000001000001000001000001000001000001000111110000011111000100100
```
[Try it online!](https://tio.run/##rZLdCsAgCIVfyfNWG@xqN3t81xJKyh@KSZhF59Os5zjvixmgYvgmSFDDutsMs1cLkYpM5ASPFNCUtokNMjrbta4jyrT71XeSLt3xaY4Nv1S31X2fP99ttV9RHhrIVv@8XNEbDgeTn6LTt1svESLSf29t9qkM5hc)
## [Whispers v1](https://github.com/cairdcoinheringaahing/Whispers/tree/v1), 29 bytes
```
> "Hello, World!"
>> Output 1
```
[Try it online!](https://tio.run/##K8/ILC5ILSr@/99OQckjNScnX0chPL8oJ0VRicvOTsG/tKSgtETB8P9/AA)
## [Whispers v2](https://github.com/cairdcoinheringaahing/Whispers), 29 bytes
```
> "Hello, World!"
>> Output 1
```
[Try it online!](https://tio.run/##K8/ILC5ILSo2@v/fTkHJIzUnJ19HITy/KCdFUYnLzk7Bv7SkoLREwfD/fwA)
## [Whitespace](https://web.archive.org/web/20150618184706/http://compsoc.dur.ac.uk/whitespace/tutorial.php), 146 bytes
```
   
  		  	 	 
  				
   	
   			
   	  
  		 	  
  		  	 		
  							
   	  
   	
 
   			 
  		   		

  
 
 
	 	
   		 	 		
	   	
  
 


  	




```
[Try it online!](https://tio.run/##VY1RCsAwCEO/4ylytVEK299ghR7fxVWhQ9RAnnGe1@jPfbTuTtJIQK36JKDFNVIXhJ1G0j8o7vKy0CAtTBUqdwUgH8kJRJyZ@ws)
## [Width](https://github.com/stestoltz/Width), 30 bytes
```
GFiUWOUQROWIJiiBAQWMJOCDMiIGUU
```
[Try it online!](https://tio.run/##K89MKcn4/9/dLTM03D80MMg/3NMrM9PJMTDc18vf2cU309M9NPT/fwA)
## [Wierd (John's)](https://github.com/catseye/Wierd), 181 bytes
```
-*******************           !dlroW ,olleH
 *
 R*   *    *     *
 E*  **    **   *
 T*  **    **  *
 U ***   ***  ****
 R   *  *  *      *
 N  *    *  ********
    *  ****
 0   **
 ```
 [Try it online!](https://tio.run/##K89MLUr5/19XCxMoIIBiSk5RfriCTn5OTqoHl4IWl0IQSBqsBKIOKOQKZEF0gUmgSAiKCFAgVAFiLpgE2QE0CGKEFswgkDI/hNEwx3Ah8bkUDMBm/P8PAA)
## [Wise](https://github.com/Wheatwizard/Wise), 135 bytes
```
~-<<<~-<<<::^~-<~-<<<~-<<~-:::^~-<<<~-^::?:>~-<~-:?::^~-<<~-<~-<<::^~-<<<<<:<::^<~-<<~-<~-<~-|!::^~-<~-<~-<<<~-<!:::^~-<<<^::^~-<<<<<~-
```
[Try it online!](https://tio.run/##K88sTv3/v07XxsYGTFhZxQFpOL9O1woiAmLGWVnZW9mBpYEMiDBUMUwRkAVi2yCk6nRrFOGGwsxVhJsah9BZp/v//3/dRAA)
## [Woefully](https://github.com/Destructible-Watermelon/Woefully) (WARNING: INCORRECT)
```
||||||||||| ||
|||||||||| |||
||||||||| ||||
|||||||| |||||
||||||| ||||||
|||||| |||||||
||||| ||||||||
||||| ||||||||
||||| ||||||||
||||| ||||||||
||||| ||||||||
||||| ||||||||
|||| |||||||||
|||| |||||||||
|||| |||||||||
|||| |||||||||
|||| |||||||||
|||| |||||||||
||| ||||||||||
||| ||||||||||
||| ||||||||||
||| ||||||||||
||| ||||||||||
|| |||||||||||
|| |||||||||||
|| |||||||||||
|| |||||||||||
|| |||||||||||
||| ||||||||||
|||| |||||||||
||||| ||||||||
|||||| |||||||
||||||| ||||||
|||||||| |||||
||||||| ||||||
|||||||| |||||
||||||||| ||||
|||||||||| |||
||||||||||| ||
|||||||||||| |
||||||||||| ||
```
[Try it online!](https://tio.run/##K89PTSvNyan8/78GARRqarhQeEhcEA/BBfPgXAgPxoXyoFwYj@pcOI/aXASPUi4Sj1IuukXoXkAPK7RYQI8j/DGILose@@hpAz3lgPhosv//AwA)
## [Wolfram Language (Mathematica)](https://www.wolfram.com/wolframscript/), 21 bytes
```
Print@"Hello, World!"
```
[Try it online!](https://tio.run/##y00syUjNTSzJTE78/z@gKDOvxEHJIzUnJ19HITy/KCdFUen/fwA)
## [wsf](https://github.com/dkudriavtsev/wsf), 174 bytes
```
 	 	 	 
 	 
 	 
 
   
   
 
  
         
  
      
  
         
 	 	 
      	 	 	  	
		  	
		       
	 
 
 
		 
 	 	 
 			 
				   
         
      		   
 	 	 

  
 				 	 
	
```
[Try it online!](https://tio.run/##XU1BDgAgCDrjK3xdH@jQ821C6UqHQ4ew5ohwsK1g7gcmourlO@ubJSuHoaZE8s3D1SM5QMkTQh@0M9MozIeIDQ)
## [Wumpus](https://github.com/m-ender/wumpus), 19 bytes
```
"!dlroW ,olleH"l&o@
```
[Try it online!](https://tio.run/##Ky/NLSgt/v9fSTElpyg/XEEnPycn1UMpRy3f4f9/AA)
## [xEec](http://paulo-jorente.de/poncho/esolang/xEec/), 64 bytes
```
h$! h$d h$l h$r h$o h$W h#32 h$, h$o h$l h$l h$e h$H >o o$ p jno
```
[Try it online!](https://tio.run/##q0hNTf7/P0NFUSFDJQWIc4C4CIjzgThcIUPZ2AjI0IEK5EBxKhB7KNjlK@SrKBQoZOXl//8PAA)
## [xeraph](https://tio.run/##q0hNTf7/P0NFUSFDJQWIc4C4CIjzgThcIUPZ2AjI0IEK5EBxKhB7KNjlK@SrKBQoZOXl//8PAA), 19 bytes
```
l?$.
~!dlroW ,olleH
```
[Try it online!](https://tio.run/##q0gtSizI@P8/x15Fj6tOMSWnKD9cQSc/JyfV4/9/AA)
## [YABALL](https://github.com/TryItOnline/yaball), 368 bytes
```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.+++++++++++++++++++++++++++++.+++++++..+++.-------------------------------------------------------------------.------------.+++++++++++++++++++++++++++++++++++++++++++++++++++++++.++++++++++++++++++++++++.+++.------.--------.-------------------------------------------------------------------.>@
```
[Try it online!](https://tio.run/##q0xMSszJ@f9fm0pAjyhZPRBDT5dygGKGHrXdjORKPaw2kutqO4f//wE)
## [Yabasic](http://www.yabasic.de/), 16 bytes
```
?"Hello, World!"
```
[Try it online!](https://tio.run/##q0xMSizOTP7/317JIzUnJ19HITy/KCdFUen/fwA)
## [yash](https://yash.osdn.jp/), 18 bytes
```
echo Hello, World!
```
[Try it online!](https://tio.run/##q0wszvj/PzU5I1/BIzUnJ19HITy/KCdF8f9/AA)
## [yup](https://github.com/ConorOBrien-Foxx/yup), 1171 bytes
```
0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--0e~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0~--~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--:::@@0e0e0~--0e0~--0~--:@0e0e0~--0e0e0~--0~--0e0e0~--0e0e0~--0~--~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@0e0e0~--0e0~--0e0e0~--~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0~--0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@@0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--0e0~--0e0e0~--0e0e0~--0~--~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@
@0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--0~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@0e0e0~--0e0~--0e0e0~--0e0~--~0e0e0~--0e0e0~--0~--0e0e0~--0e0~--0~--0e0e0~--0e0~--0~--|~|0~--e0~--@
```
[Try it online!](https://tio.run/##qywt@P/fIBUI63R14TQyG0OkjjTlCJGauhoQBeY7kGuIQepA20@kPmqFlJWVlYMDphIrQj6Ai1E9vAYuLRAd/tRxFyWJhKaRQb7DaJkYqJkk/v8HAA)
## [Zephyr](https://github.com/dloscutoff/zephyr), 20 bytes
```
print"Hello, World!"
```
[Try it online!](https://tio.run/##q0otyKgs@v@/oCgzr0TJIzUnJ19HITy/KCdFUen/fwA)
## [Zig](https://ziglang.org/), 88 bytes
```
pub fn main()!void{try(try@import("std").io.getStdOut()).write("Hello, World!");}
```
[Try it online!](https://tio.run/##DcOxCoAgEADQX1GnOwh/oKWxraGhudDkQLuwq6jo260H76ZQyrpPal5UGmkB1AeTeyRf8G8orZwFzCbOoCW2wUsvrtsFEO2ZSTyY1sfIlRo4R6cN1m8pHw)
## [zkl](http://www.zenkinetic.com/zkl.html), 22 bytes
```
print("Hello, World!")
```
[Try it online!](https://tio.run/##q8rO@f@/oCgzr0RDySM1JydfRyE8vygnRVFJ8/9/AA)
## [Zsh](https://www.zsh.org/), 17 bytes
```
<<<Hello,\ World!
```
[Try it online!](https://tio.run/##qyrO@P/fxsbGIzUnJ18nRiE8vygnRfH/fwA)

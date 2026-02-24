![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/98d5bcf99b03142a1da139b0bdb7992fe0bd6029ebb1d59136c7aac919ad111c.jpg)


# The Isabelle/Isar Reference Manual

Makarius Wenzel 

With Contributions by Clemens Ballarin, Stefan Berghofer, Jasmin Blanchette, Timothy Bourke, Lukas Bulwahn, Amine Chaieb, Lucas Dixon, Florian Haftmann, Brian Huffman, Lars Hupel, Gerwin Klein, Alexander Krauss, Ondřej Kunčar, Andreas Lochbihler, Tobias Nipkow, Lars Noschinski, David von Oheimb, Larry Paulson, Sebastian Skalberg, Christian Sternagel, Dmitriy Traytel 

May 23, 2024 

# Preface

The Isabelle system essentially provides a generic infrastructure for building deductive systems (programmed in Standard ML), with a special focus on interactive theorem proving in higher-order logics. Many years ago, even endusers would refer to certain ML functions (goal commands, tactics, tacticals etc.) to pursue their everyday theorem proving tasks. 

In contrast Isar provides an interpreted language environment of its own, which has been specifically tailored for the needs of theory and proof development. Compared to raw ML, the Isabelle/Isar top-level provides a more robust and comfortable development platform, with proper support for theory development graphs, managed transactions with unlimited undo etc. 

In its pioneering times, the Isabelle/Isar version of the Proof General user interface [2, 3] has contributed to the success of for interactive theory and proof development in this advanced theorem proving environment, even though it was somewhat biased towards old-style proof scripts. The more recent Isabelle/jEdit Prover IDE [61] emphasizes the document-oriented approach of Isabelle/Isar again more explicitly. 

Apart from the technical advances over bare-bones ML programming, the main purpose of the Isar language is to provide a conceptually different view on machine-checked proofs [58, 59]. Isar stands for Intelligible semiautomated reasoning. Drawing from both the traditions of informal mathematical proof texts and high-level programming languages, Isar offers a versatile environment for structured formal proof documents. Thus properly written Isar proofs become accessible to a broader audience than unstructured tactic scripts (which typically only provide operational information for the machine). Writing human-readable proof texts certainly requires some additional efforts by the writer to achieve a good presentation, both of formal and informal parts of the text. On the other hand, human-readable formal texts gain some value in their own right, independently of the mechanic proof-checking process. 

Despite its grand design of structured proof texts, Isar is able to assimilate the old tactical style as an “improper” sub-language. This provides an easy upgrade path for existing tactic scripts, as well as some means for interactive experimentation and debugging of structured proofs. Isabelle/Isar supports 

a broad range of proof styles, both readable and unreadable ones. 

The generic Isabelle/Isar framework (see chapter 2) works reasonably well for any Isabelle object-logic that conforms to the natural deduction view of the Isabelle/Pure framework. Specific language elements introduced by Isabelle/HOL are described in part III. Although the main language elements are already provided by the Isabelle/Pure framework, examples given in the generic parts will usually refer to Isabelle/HOL. 

Isar commands may be either proper document constructors, or improper commands. Some proof methods and attributes introduced later are classified as improper as well. Improper Isar language elements, which are marked by “∗” in the subsequent chapters; they are often helpful when developing proof documents, but their use is discouraged for the final human-readable outcome. Typical examples are diagnostic commands that print terms or theorems according to the current context; other commands emulate oldstyle tactical theorem proving. 

# Contents

# I Basic Concepts 1

# 1 Synopsis 2

1.1 Notepad . . . 2 

1.1.1 Types and terms . . 2 

1.1.2 Facts . . . . 2 

1.1.3 Block structure . . . 5 

1.2 Calculational reasoning 6 

1.2.1 Special names in Isar proofs . . . . 6 

1.2.2 Transitive chains . . . . 7 

1.2.3 Degenerate calculations . . . . 8 

1.3 Induction 9 

1.3.1 Induction as Natural Deduction . . . . 9 

1.3.2 Induction with local parameters and premises . . . . . 11 

1.3.3 Implicit induction context . . . 12 

1.3.4 Advanced induction with term definitions . . . . . . . . 12 

1.4 Natural Deduction 13 

1.4.1 Rule statements . . . . . . 13 

1.4.2 Isar context elements . . . . . . 14 

1.4.3 Pure rule composition 15 

1.4.4 Structured backward reasoning . . . . . . 16 

1.4.5 Structured rule application . . . . . . . 17 

1.4.6 Example: predicate logic . . . . . 18 

1.5 Generalized elimination and cases . . . . 21 

1.5.1 General elimination rules . . . . . . . 21 

1.5.2 Rules with cases . . . . 22 

1.5.3 Elimination statements and case-splitting . . . . . . . . 24 

1.5.4 Obtaining local contexts . . . 24 

# 2 The Isabelle/Isar Framework 26

2.1 The Pure framework . . . . . 29 

2.1.1 Primitive inferences . . . . 30 

2.1.2 Reasoning with rules . . . . 30 

2.2 The Isar proof language . . 32 

2.2.1 Context elements . . . . . . . . 34 

2.2.2 Structured statements . . . . . 36 

2.2.3 Structured proof refinement . . . 37 

2.2.4 Calculational reasoning 38 

2.3 Example: First-Order Logic . . . 39 

2.3.1 Equational reasoning . . . . 40 

2.3.2 Basic group theory . . . . . . 41 

2.3.3 Propositional logic . . . 42 

2.3.4 Classical logic . . . . . 44 

2.3.5 Quantifiers 45 

2.3.6 Canonical reasoning patterns . . 46 

# II General Language Elements 50

# 3 Outer syntax — the theory language 51

3.1 Commands 51 

3.2 Lexical matters . . . 52 

3.3 Common syntax entities . . 54 

3.3.1 Names . . . . . 54 

3.3.2 Numbers . . . . . . 55 

3.3.3 Embedded content . . . . . 55 

3.3.4 Document text . . . 56 

3.3.5 Document comments . . . 56 

3.3.6 Type classes, sorts and arities . . . . 57 

3.3.7 Types and terms . . 58 

3.3.8 Term patterns and declarations . . . . 60 

3.3.9 Attributes and theorems . . . 62 

3.3.10 Structured specifications . . . . 65 

3.4 Diagnostic commands . . . . 66 

# 4 Document preparation 70

4.1 Markup commands . . . 70 

4.2 Document antiquotations . . 72 

4.2.1 Styled antiquotations . . . . 80 

4.2.2 General options . . . . . 81 

4.3 Markdown-like text structure . . . . 82 

4.4 Document markers and command tags . . 83 

4.5 Railroad diagrams . . . . 86 

# 5 Specifications 91

5.1 Defining theories 91 

5.2 Local theory targets . . 94 

5.3 Bundled declarations . . . 96 

5.4 Term definitions 98 

5.5 Axiomatizations . . 100 

5.6 Generic declarations . . 101 

5.7 Locales . . 102 

5.7.1 Locale expressions . . 102 

5.7.2 Locale declarations . . . . . . . . 104 

5.7.3 Locale interpretation . . . . . . . . 108 

5.8 Classes . . . . 113 

5.8.1 The class target . . . . . . 116 

5.8.2 Co-regularity of type classes and arities . . . . . . . . . 116 

5.9 Overloaded constant definitions . . . . 117 

5.10 Incorporating ML code . . 119 

5.11 Generated files and exported files . . . . . 123 

5.12 Primitive specification elements . . . . . 127 

5.12.1 Sorts . . . . . . . . 127 

5.12.2 Types . . . . . 127 

5.13 Naming existing theorems . . . . 128 

5.14 Oracles . . 129 

5.15 Name spaces . . . . . . 130 

# 6 Proofs 131

6.1 Proof structure . . . . . 131 

6.1.1 Formal notepad . . . . . . 131 

6.1.2 Blocks . . . . . . . . 132 

6.1.3 Omitting proofs . . . . . . 133 

6.2 Statements . . . . . 133 

6.2.1 Context elements . . . . . . 133 

6.2.2 Term abbreviations . . . 135 

6.2.3 Facts and forward chaining . . . . 136 

6.2.4 Goals . . . . . . . 138 

6.3 Calculational reasoning . . 142 

6.4 Refinement steps . . 144 

6.4.1 Proof method expressions . . . . 144 

6.4.2 Initial and terminal proof steps . . . . . . . 146 

6.4.3 Fundamental methods and attributes . . . . . . . . . . 148 

6.4.4 Defining proof methods . . . . . . . . . 152 

6.5 Proof by cases and induction . . . . . 153 

6.5.1 Rule contexts . . . . . 153 

6.5.2 Proof methods . . . . . . 156 

6.5.3 Declaring rules . . . . . 161 

6.6 Generalized elimination and case splitting . . . . . . . . . . . 162 

7 Proof scripts 166 

7.1 Commands for step-wise refinement . . 166 

7.2 Explicit subgoal structure . . . . . 168 

7.3 Tactics: improper proof methods . . . . 170 

8 Inner syntax — the term language 174 

8.1 Printing logical entities . . . . . 174 

8.1.1 Diagnostic commands . . . 174 

8.1.2 Details of printed content . . . . . . 177 

8.1.3 Alternative print modes . . . . . 179 

8.2 Mixfix annotations . . . . . . . 180 

8.2.1 The general mixfix form . . . . . . . . 181 

8.2.2 Infixes . . . . . . . . . 184 

8.2.3 Binders . . 184 

8.3 Explicit notation . . . . 185 

8.4 The Pure syntax . . . . 186 

8.4.1 Lexical matters . . . . . . . . 186 

8.4.2 Priority grammars . . . . . . . . . 187 

8.4.3 The Pure grammar . . . . . . 188 

8.4.4 Inspecting the syntax . . . . . . . 192 

8.4.5 Ambiguity of parsed expressions . . . . . . . . . . . . . 193 

8.5 Syntax transformations . . 193 

8.5.1 Abstract syntax trees . . . 194 

8.5.2 Raw syntax and translations . . 197 

8.5.3 Syntax translation functions . . . . 202 

8.5.4 Built-in syntax transformations . . . . . . . . . . . . . 204 

# 9 Generic tools and packages 207

9.1 Configuration options . . . 207 

9.2 Basic proof tools . . 208 

9.2.1 Miscellaneous methods and attributes . . . . . . . . . 208 

9.2.2 Low-level equational reasoning . . . . . . . . 211 

9.3 The Simplifier . . 213 

9.3.1 Simplification methods . . 213 

9.3.2 Declaring rules . . . . . . . . 218 

9.3.3 Ordered rewriting with permutative rules . . . . . . . . 221 

9.3.4 Simplifier tracing and debugging . . . . . . 223 

9.3.5 Simplification procedures . . 225 

9.3.6 Configurable Simplifier strategies . . . . . . . . . . . 228 

9.3.7 Forward simplification . . . . . 232 

9.4 The Classical Reasoner . . . 233 

9.4.1 Basic concepts . . . . . . . 233 

9.4.2 Rule declarations . . . . . . 237 

9.4.3 Structured methods . . . . . . 239 

9.4.4 Fully automated methods . . . . . . . . 239 

9.4.5 Partially automated methods . . . . 243 

9.4.6 Single-step tactics . . . . . . . 244 

9.4.7 Modifying the search step . . . . 245 

9.5 Object-logic setup . . 246 

9.6 Tracing higher-order unification . . . . . . . . . 248 

# III Isabelle/HOL 250

# 10 Higher-Order Logic 251

# 11 Derived specification elements 253

11.1 Inductive and coinductive definitions . . . . . . . 253 

11.1.1 Derived rules . . . . . . 255 

11.1.2 Monotonicity theorems . . . . . . 255 

11.2 Recursive functions . . 257 

11.2.1 Proof methods related to recursive definitions . . . . . 262 

11.2.2 Functions with explicit partiality . . . . . . 263 

11.2.3 Old-style recursive function definitions (TFL) . . . . . 264 

11.3 Adhoc overloading of constants . . . . . 266 

11.4 Definition by specification . . . . . 267 

11.5 Old-style datatypes . . 267 

11.6 Records . . 269 

11.6.1 Basic concepts . . . . . . 269 

11.6.2 Record specifications . . . . . . . 270 

11.6.3 Record operations . . . . . . . 272 

11.6.4 Derived rules and proof tools . . . . 273 

11.7 Semantic subtype definitions . . 274 

11.8 Functorial structure of types . . . . . . 277 

11.9 Quotient types with lifting and transfer . . . . . . . . . . . . 278 

11.9.1 Quotient type definition . . . . 278 

11.9.2 Lifting package . . . . . . 279 

11.9.3 Transfer package . . . . 285 

11.9.4 Old-style definitions for quotient types . . . . . . . . . 288 

# 12 Proof tools 291

12.1 Proving propositions . . . . . 291 

12.2 Checking and refuting propositions . . . . . 293 

12.3 Coercive subtyping . . . . . . 298 

12.4 Arithmetic proof support . . . . . . 299 

12.5 Intuitionistic proof search . . . . 300 

12.6 Model Elimination and Resolution . . . . . 300 

# CONTENTS

ix 

12.7 Algebraic reasoning via Gröbner bases . . . . . . . . . . . . 301 

12.8 Coherent Logic . . . . . . . 302 

12.9 Unstructured case analysis and induction . . . . . . . . . . 303 

12.10Adhoc tuples . . 304 

# 13 Executable code 306

# IV Appendix 319

# A Isabelle/Isar quick reference 320

A.1 Proof commands . . 320 

A.1.1 Main grammar . . . . 320 

A.1.2 Primitives . . . . . . . . 321 

A.1.3 Abbreviations and synonyms . . . . . . . 321 

A.1.4 Derived elements . . . . . . . . 321 

A.1.5 Diagnostic commands . . . . . . . . 322 

A.2 Proof methods . . . . . . . . 322 

A.3 Attributes . . . . . . . 323 

A.4 Rule declarations and methods . . . . . . . . 323 

A.5 Proof scripts . . . . . 324 

A.5.1 Commands . . . . . . . 324 

A.5.2 Methods . . . . . . . . 324 

# B Predefined Isabelle symbols 325

# Bibliography 331

# Index 337

# List of Figures

2.1 Natural Deduction via inferences according to Gentzen, rules in Isabelle/Pure, and proofs in Isabelle/Isar . . . 27 

2.2 Main grammar of the Isar proof language . . . . . 48 

2.3 Isar/VM modes . . . . 49 

8.1 Parsing and printing with translations . . 194 

# Part I

# Basic Concepts

# Synopsis

# 1.1 Notepad

An Isar proof body serves as mathematical notepad to compose logical content, consisting of types, terms, facts. 

# 1.1.1 Types and terms

notepad begin 

Locally fixed entities: 

fix x — local constant, without any type information yet fix $x : \iota _ { a }$ — variant with explicit type-constraint for subsequent use 

fix a b assume $a = b$ — type assignment at first occurrence in concrete term 

Definitions (non-polymorphic): 

define $x : \iota _ { a }$ where $x = t$ 

Abbreviations (polymorphic): 

let $\ell f = \lambda x$ . x term $\it { ? 4 } \ : \it { ! 4 }$ 

Notation: 

write x $( * * * )$ end 

# 1.1.2 Facts

A fact is a simultaneous list of theorems. 

# Producing facts

notepad 

begin 

Via assumption (“lambda”): 

assume a: A 

Via proof (“let”): 

have b: B hproof i 

Via abbreviation (“let”): 

note $c = a$ b 

end 

# Referencing facts

notepad 

begin 

Via explicit name: 

assume a: A 

note a 

Via implicit name: 

assume A 

note this 

Via literal proposition (unification with results from the proof text): 

assume A 

note ‹A› 

assume $\Lambda x . \textit { B x }$ 

note ‹B a› 

note $\textit { ering } \textit { ering } \textit { ering } \textit { ering } \textit { ering } \textit { ering } \textit { ering } b \rangle$ 

end 

# Manipulating facts

notepad 

begin 

Instantiation: 

assume $a\colon \bigwedge x$ . $Bx$ note $a$ note $a$ [of $b]$ note $a$ [where $x = b]$ 

Backchaining: 

assume 1: $A$ assume 2: $A\Rightarrow C$ note 2 [OF 1]   
note 1 [THEN 2] 

Symmetric results: 

assume $x = y$ note this [symmetric] 

assume $x\neq y$ note this [symmetric] 

Adhoc-simplification (take care!): assume $P([@xs)$ note this [simplified]   
end 

# Projections

Isar facts consist of multiple theorems. There is notation to project interval ranges. 

```txt
notepad   
begin assume stuff:ABCD note stuff(1) note stuff(2-3) note stuff(2-)   
end 
```

# Naming conventions

• Lower-case identifiers are usually preferred. 

• Facts can be named after the main term within the proposition. 

• Facts should not be named after the command that introduced them (assume, have). This is misleading and hard to maintain. 

• Natural numbers can be used as “meaningless” names (more appropriate than a1, a2 etc.) 

• Symbolic identifiers are supported (e.g. ∗, ∗∗, ∗∗∗). 

# 1.1.3 Block structure

The formal notepad is block structured. The fact produced by the last entry of a block is exported into the outer context. 

notepad   
begin { have $a$ .. $A$ (proof) have $b$ .. $B$ (proof) note a b } note this note $\langle A\rangle$ note $\langle B\rangle$ end 

Explicit blocks as well as implicit blocks of nested goal statements (e.g. have) automatically introduce one extra pair of parentheses in reserve. The next command allows to “jump” between these sub-blocks. 

notepad   
begin   
{ have $a$ ..A $\langle$ proof $\rangle$ next have $b$ .. $B$ proof - show $B$ $\langle$ proof $\rangle$ next have $c$ .. $C$ $\langle$ proof $\rangle$ next have $d$ .. $D$ $\langle$ proof $\rangle$ qed   
} 

Alternative version with explicit parentheses everywhere: 

```txt
{ have a: A <proof> } { have b: B proof - show B <proof> } have c: C <proof> } have d: D <proof> } qed } end 
```

# 1.2 Calculational reasoning

For example, see ~~/src/HOL/Isar_Examples/Group.thy. 

# 1.2.1 Special names in Isar proofs

• term ?thesis — the main conclusion of the innermost pending claim 

• term . . . — the argument of the last explicitly stated result (for infix application this is the right-hand side) 

• fact this — the last result produced in the text 

notepad   
begin   
have $x = y$ proof - term ?thesis show ?thesis (proof) term ?thesis - static! 

```txt
qed term ... thm this end 
```

Calculational reasoning maintains the special fact called “calculation” in the background. Certain language elements combine primary this with secondary calculation. 

# 1.2.2 Transitive chains

The Idea is to combine this and calculation via typical trans rules (see also print_trans_rules): 

```txt
thm trans  
thm less_trans  
thm less_le_trans 
```

```txt
notepad begin 
```

Plain bottom-up calculation: 

have $a = b$ (proof)  
also  
have $b = c$ (proof)  
also  
have $c = d$ (proof)  
finally  
have $a = d$ . 

Variant using the . . . abbreviation: 

have $a = b$ (proof)  
also  
have $\ldots = c$ (proof)  
also  
have $\ldots = d$ (proof)  
finally  
have $a = d$ . 

Top-down version with explicit claim at the head: 

have $a = d$ proof -   
have $a = b$ （proof> 

also have $\dots = c$ (proof) also have $\dots = d$ (proof) finally show ?thesis . qed next Mixed inequalities (require suitable base type): fix abcd::nat have $a <   b$ (proof) also have $b\leq c$ (proof) also have $c = d$ (proof) finally have $a <   d$ .   
end 

# Notes

• The notion of trans rule is very general due to the flexibility of Isabelle/Pure rule composition. 

• User applications may declare their own rules, with some care about the operational details of higher-order unification. 

# 1.2.3 Degenerate calculations

The Idea is to append this to calculation, without rule composition. This is occasionally useful to avoid naming intermediate facts. 

notepad begin 

A vacuous proof: 

have $A$ (proof) moreover have $B$ (proof) moreover 

have $C$ <proof> ultimately have $A$ and $B$ and $C$ . next 

Slightly more content (trivial bigstep reasoning): 

have $A\langle \text{proof}\rangle$ moreover  
have $B\langle \text{proof}\rangle$ moreover  
have $C\langle \text{proof}\rangle$ ultimately  
have $A\wedge B\wedge C$ by blast  
end 

Note that For multi-branch case splitting, it is better to use consider. 

# 1.3 Induction

# 1.3.1 Induction as Natural Deduction

In principle, induction is just a special case of Natural Deduction (see also §1.4). For example: 

```txt
thm nat.induct  
print_statement nat.induct 
```

notepad   
begin fix $n$ :nat have $P n$ proof (rule nat.induct) - fragile rule application! show $P0\langle \text{proof}\rangle$ next fix $n$ :nat assume $P n$ show $P$ (Suc n) <proof> qed   
end 

In practice, much more proof infrastructure is required. 

The proof method induct provides: 

• implicit rule selection and robust instantiation 

• context elements via symbolic case names 

• support for rule-structured induction statements, with local parameters, premises, etc. 

```txt
notepad   
begin fix n::nat have Pn proof (induct n) case 0 show ?case <proof> next case (Suc n) from Suc.hyps show ?case <proof> qed   
end 
```

# Example

The subsequent example combines the following proof patterns: 

• outermost induction (over the datatype structure of natural numbers), to decompose the proof problem in top-down manner 

• calculational reasoning (§1.2) to compose the result in each case 

• solving local claims within the calculation by simplification 

lemma  
fixes $n :: \text{nat}$ shows $(\sum i = 0..n. i) = n * (n + 1)$ div 2  
proof (induct $n$ )  
case 0  
have $(\sum i = 0..0. i) = (0::\text{nat})$ by simp  
also have $\ldots = 0 * (0 + 1)$ div 2 by simp  
finally show ?case .  
next  
case (Suc $n$ )  
have $(\sum i = 0..\text{Suc } n. i) = (\sum i = 0..n. i) + (n + 1)$ by simp  
also have $\ldots = n * (n + 1)$ div 2 + (n + 1) by (simp add: Suc.hyps)  
also have $\ldots = (n * (n + 1) + 2 * (n + 1))$ div 2 by simp  
also have $\ldots = (\text{Suc } n * (\text{Suc } n + 1))$ div 2 by simp 

finally show ?case . 

qed 

This demonstrates how induction proofs can be done without having to consider the raw Natural Deduction structure. 

# 1.3.2 Induction with local parameters and premises

Idea: Pure rule statements are passed through the induction rule. This achieves convenient proof patterns, thanks to some internal trickery in the induct method. 

Important: Using compact HOL formulae with $\forall / \longrightarrow$ is a well-known antipattern! It would produce useless formal noise. 


notepad



begin


fix $n::nat$ fix $P::nat\Rightarrow bool$ fix $Q::'a\Rightarrow nat\Rightarrow$ 

have $Pn$ proof (induct $n$ 1   
case O   
show $P0\langle \text{proof}\rangle$ next   
case (Suc n)   
from $\langle Pn\rangle$ show $P$ (Suc n) (proof)   
qed 

have $A n \Rightarrow P n$ proof (induct $n$ )  
    case 0  
    from $\langle A 0 \rangle$ show $P 0 \langle \text{proof} \rangle$ next  
    case (Suc $n$ )  
    from $\langle A n \Rightarrow P n \rangle$ and $\langle A (\text{Suc} n) \rangle$ show $P (\text{Suc} n) \langle \text{proof} \rangle$ qed 

have $\wedge x$ . $Qxn$ proof (induct $n$ ）  
case0show $Qx0\langle \text{proof}\rangle$ 

next case (Suc n) from $\langle \bigwedge x.Qxn\rangle$ show $Qx$ (Suc n) (proof) 

Local quantification admits arbitrary instances: 

note $\langle Q a n\rangle$ and $\langle Q b n\rangle$ qed end 

# 1.3.3 Implicit induction context

The induct method can isolate local parameters and premises directly from the given statement. This is convenient in practical applications, but requires some understanding of what is going on internally (as explained above). 

notepad   
begin fix $n:_{\cdot}$ nat fix $Q:a\Rightarrow n a t\Rightarrow b o o l$ fix $x:a$ assume $A x n$ then have $Qx n$ proof (induct n arbitrary: $x$ ) case 0 from $\langle A x 0\rangle$ show $Qx0\langle \text{proof}\rangle$ next case (Suc n) from $\langle \bigwedge x.Axn\Longrightarrow Qxn\rangle$ -arbitrary instances can be produced here and $\langle A x(Suc n)\rangle$ show $Qx(Suc n)\langle \text{proof}\rangle$ qed   
end 

# 1.3.4 Advanced induction with term definitions

Induction over subexpressions of a certain shape are delicate to formalize. The Isar induct method provides infrastructure for this. 

Idea: sub-expressions of the problem are turned into a defined induction variable; often accompanied with fixing of auxiliary parameters in the original expression. 

```txt
notepad begin 
```

fix $a\because 'a\Rightarrow nat$ fix $A\because nat\Rightarrow bool$ assume $A(ax)$ then have $P(a x)$ proof (induct ax arbitrary: $x$ 1 case 0 note prem $\equiv$ A $(a x)\rangle$ and defn $\equiv$ 0=a x> show $P(a x)\langle \text{proof}\rangle$ next case (Suc n) note hyp $\equiv$ A $\backslash x$ . $n = a x\Longrightarrow A(a x)\Longrightarrow P(a x)\rangle$ and prem $\equiv$ A $(a x)\rangle$ and defn $\equiv$ Suc $n = a x >$ show $P(a x)\langle \text{proof}\rangle$ qed   
end 

# 1.4 Natural Deduction

# 1.4.1 Rule statements

Isabelle/Pure “theorems” are always natural deduction rules, which sometimes happen to consist of a conclusion only. 

The framework connectives $\Lambda$ and $\Longrightarrow$ indicate the rule structure declaratively. For example: 

```txt
thm conjI  
thm impI  
thm nat.induct 
```

The object-logic is embedded into the Pure framework via an implicit derivability judgment $T r u e p r o p : : \ : b o o l \Rightarrow p r o p .$ . 

Thus any HOL formulae appears atomic to the Pure framework, while the rule structure outlines the corresponding proof pattern. 

This can be made explicit as follows: 

```txt
notepad   
begin   
write Trueprop (Tr) 
```

thm conjI 

```txt
thm impI thm nat.Induct end 
```

Isar provides first-class notation for rule statements as follows. 

```txt
print_statement conjI  
print_statement impI  
print_statement nat.Induct 
```

# Examples

Introductions and eliminations of some standard connectives of the objectlogic can be written as rule statements as follows. (The proof “by blast” serves as sanity check.) 

lemma $P \implies F a l s e ) \implies \neg ~ P$ by blast 

lemma $\neg \ P \Longrightarrow P \Longrightarrow Q$ by blast 

lemma $P \implies Q \implies P \land Q$ by blast lemma P ∧ Q =⇒ (P =⇒ Q =⇒ R) =⇒ R by blast 

lemma $P \Longrightarrow P \vee Q$ by blast lemma $Q \Longrightarrow P \vee Q$ by blast lemma $P \lor Q \implies ( P \implies R ) \implies ( Q \implies R ) \implies R$ by blast 

lemma $( \land x . \ P \ x ) \implies ( \forall x . \ P \ x )$ by blast lemma $( \forall x . \ P \ x ) \Longrightarrow \ P \ x$ by blast 

lemma $\textit { P x } \Longrightarrow ( \exists x . \textit { P x } )$ by blast lemma $( \exists x . \ P \ x ) \Longrightarrow ( \bigwedge x . \ P \ x \Longrightarrow R ) \Longrightarrow R$ by blast 

lemma $x \in A \Longrightarrow x \in B \Longrightarrow x \in A \cap B$ by blast lemma x ∈ A ∩ B =⇒ $x \in A \Longrightarrow x \in B \Longrightarrow R ) \Longrightarrow R$ by blast 

lemma $x \in A \Longrightarrow x \in A \cup B$ by blast lemma $x \in B \Longrightarrow x \in A \cup B$ by blast lemma x ∈ A ∪ B =⇒ $( x \in A \Longrightarrow R ) \Longrightarrow ( x \in B \Longrightarrow R ) \Longrightarrow R$ by blast 

# 1.4.2 Isar context elements

We derive some results out of the blue, using Isar context elements and some explicit blocks. This illustrates their meaning wrt. Pure connectives, without goal states getting in the way. 

notepad   
begin { fix $x$ have $Bx\langle \mathrm{proof}\rangle$ 1 have $\wedge x$ . $Bx$ by fact   
next { assume A have $B\langle \mathrm{proof}\rangle$ 1 have $A\Rightarrow B$ by fact   
next { define $x$ where $x = t$ have $Bx\langle \mathrm{proof}\rangle$ 1 have $Bt$ by fact   
next { obtain $x:^\prime a$ where $Bx\langle \mathrm{proof}\rangle$ have $C\langle \mathrm{proof}\rangle$ 1 have $C$ by fact   
end 

# 1.4.3 Pure rule composition

The Pure framework provides means for: 

• backward-chaining of rules by resolution 

• closing of branches by assumption 

Both principles involve higher-order unification of $\lambda$ -terms modulo αβη- equivalence (cf. Huet and Miller). 

notepad   
begin assume $a$ .. $A$ and $b$ .. $B$ thm conjI thm conjI [of A B] -- instantiation thm conjI [of A B, OF a b] -- instantiation and composition thm conjI [OF a b] -- composition via unification (trivial) thm conjI [OF $\langle A\rangle \langle B\rangle ]$ thm conjI [OF disjI1]   
end 

Note: Low-level rule composition is tedious and leads to unreadable / unmaintainable expressions in the text. 

# 1.4.4 Structured backward reasoning

Idea: Canonical proof decomposition via fix / assume / show, where the body produces a natural deduction rule to refine some goal. 

notepad   
begin   
fix $A B::'a\Rightarrow bool$ have $\bigwedge x$ . $A x\Longrightarrow B x$ proof - fix $x$ assume $A x$ show $Bx$ (proof)   
qed   
have $\bigwedge x$ . $A x\Longrightarrow B x$ proof - { fix $x$ assume $A x$ show $Bx$ (proof)} $-$ implicit block structure made explicit note $\langle \bigwedge x$ . $A x\Longrightarrow B x\rangle$ side exit for the resulting rule   
qed   
end 

# 1.4.5 Structured rule application

Idea: Previous facts and new claims are composed with a rule from the context (or background library). 

notepad   
begin assume $r_1\colon A\Rightarrow B\Rightarrow C$ - simple rule (Horn clause) have $A$ <proof $\rangle$ - prefix of facts via outer sub-proof then have $C$ proof (rule $r_1$ ) show $B$ <proof $\rangle$ - remaining rule premises via inner sub-proof qed have $C$ proof (rule $r_1$ ) show $A$ <proof> show $B$ <proof> qed have $A$ and $B$ <proof> then have $C$ proof (rule $r_1$ ) qed have $A$ and $B$ <proof> then have $C$ by (rule $r_1$ ) next assume $r_2\colon A\Rightarrow (\bigwedge x.B_1x\Rightarrow B_2x)\Rightarrow C$ - nested rule have $A$ <proof> then have $C$ proof (rule $r_2$ ) fix $x$ assume $B_{1}x$ show $B_{2}x$ <proof> qed 

The compound rule premise $\Lambda x$ $\Lambda x . \ B _ { 1 } \ x \implies B _ { 2 } \ x$ is better addressed via fix / assume / show in the nested proof body. 

end 

# 1.4.6 Example: predicate logic

Using the above principles, standard introduction and elimination proofs of predicate logic connectives of HOL work as follows. 

notepad   
begin have $A\longrightarrow B$ and $A$ (proof) then have $B$ .. 

have $A\langle \text{proof}\rangle$ then have $A\vee B\ldots$ 

have $B\langle \text{proof}\rangle$ then have $A\vee B\ldots$ 

have $A\lor B$ (proof)   
then have $C$ proof assume $A$ then show $C$ (proof)   
next assume $B$ then show $C$ (proof)   
qed 

have $A$ and $B\langle \text{proof}\rangle$ then have $A\wedge B$ . 

have $A\wedge B$ (proof) then have $A$ .. 

have $A\wedge B$ (proof) then have $B$ .. 

have False <proof> then have $A$ . 

```txt
have True .. 
```

have $\neg A$ proof assume $A$ then show False (proof) 

qed 

have ¬ A and A hproof i 

then have $B$ .. 

have ∀ x. P x 

proof 

fix $x$ 

show P x hproof i 

qed 

have ∀ x. P x hproof i 

then have $P$ a .. 

have ∃ x. P x 

proof 

show P a hproof i 

qed 

have ∃ x. P x hproof i 

then have $C$ 

proof 

fix a 

assume P a 

show $C$ hproof i 

qed 

Less awkward version using obtain: 

have ∃ x. P x hproof i 

then obtain a where $P$ a .. 

end 

Further variations to illustrate Isar sub-proofs involving show: 

notepad 

begin 

have $A \land B$ 

proof — two strictly isolated subproofs 

show A hproof i 

next 

show B hproof i 

qed 

have A ∧ B 

proof - one simultaneous sub-proof show $A$ and $B$ (proof) qed   
have $A\wedge B$ proof - two subproofs in the same context show $A$ (proof) show $B$ (proof) qed   
have $A\wedge B$ proof - swapped order show $B$ (proof) show $A$ (proof) qed   
have $A\wedge B$ proof - sequential subproofs show $A$ (proof) show $B$ using $\langle A\rangle$ (proof) qed   
end 

# Example: set-theoretic operators

There is nothing special about logical connectives (∧, ∨, ∀ , ∃ etc.). Operators from set-theory or lattice-theory work analogously. It is only a matter of rule declarations in the library; rules can be also specified explicitly. 

notepad   
begin have $x\in A$ and $x\in B$ (proof) then have $x\in A\cap B$ .. have $x\in A$ (proof) then have $x\in A\cup B$ .. have $x\in B$ (proof) then have $x\in A\cup B$ .. have $x\in A\cup B$ (proof) then have $C$ proof assume $x\in A$ 

then show $C$ (proof)  
next  
assume $x \in B$ then show $C$ (proof)  
qed  
next  
have $x \in \bigcap A$ proof  
fix $a$ assume $a \in A$ show $x \in a$ (proof)  
qed  
have $x \in \bigcap A$ (proof)  
then have $x \in a$ proof  
show $a \in A$ (proof)  
qed  
have $a \in A$ and $x \in a$ (proof)  
then have $x \in \bigcup A$ .  
have $x \in \bigcup A$ (proof)  
then obtain $a$ where $a \in A$ and $x \in a$ .  
end 

# 1.5 Generalized elimination and cases

# 1.5.1 General elimination rules

The general format of elimination rules is illustrated by the following typical representatives: 

$\mathbf{thm}exE$ -local parameter $\mathbf{thm}conjE$ -local premises $\mathbf{thm}disjE$ -split into cases 

Combining these characteristics leads to the following general scheme for elimination rules with cases: 

• prefix of assumptions (or “major premises”) 

• one or more cases that enable to establish the main conclusion in an augmented context 

notepad   
begin   
assume $r$ .. $A_{1}\Rightarrow A_{2}\Rightarrow -$ assumptions $(\bigwedge x y.B_{1}x y\Rightarrow C_{1}x y\Rightarrow R)\Rightarrow -$ case 1 $(\bigwedge x y.B_{2}x y\Rightarrow C_{2}x y\Rightarrow R)\Rightarrow -$ case 2 $R$ -main conclusion   
have $A_{1}$ and $A_{2}$ (proof)   
then have $R$ proof (rule $r$ ) fix $xy$ assume $B_{1}x y$ and $C_1x y$ show ?thesis (proof)   
next fix $xy$ assume $B_{2}x y$ and $C_2x y$ show ?thesis (proof)   
qed   
end 

Here ?thesis is used to refer to the unchanged goal statement. 

# 1.5.2 Rules with cases

Applying an elimination rule to some goal, leaves that unchanged but allows to augment the context in the sub-proof of each case. 

Isar provides some infrastructure to support this: 

• native language elements to state eliminations 

• symbolic case names 

• method cases to recover this structure in a sub-proof 

```txt
print_statement exE  
print_statement conjE  
print_statement disjE 
```

# lemma

assumes $A_{1}$ and $A_{2}$ — assumptions  
obtains $(\text{case}_1)$ $xy$ where $B_{1}xy$ and $C_{1}xy$ $|(\text{case}_2)$ $xy$ where $B_{2}xy$ and $C_{2}xy$ $\langle \text{proof} \rangle$ 

# Example

lemma tertium_non_datur: obtains $(T)A$ $|(F)\neg A$ by blast 

# notepad

begin  
fix $x y :: {}^{\prime}a$ have $C$ proof (cases $x = y$ rule: tertium_non_datur)  
case $T$ from $\langle x = y\rangle$ show ?thesis <proof>  
next  
case $F$ from $\langle x \neq y\rangle$ show ?thesis <proof>  
qed  
end 

# Example

Isabelle/HOL specification mechanisms (datatype, inductive, etc.) provide suitable derived cases rules. 

```txt
datatype foo = Foo | Bar foo 
```

# notepad

# begin

fix $x::foo$ have $C$ proof (cases $x$ ） case Foo from $\langle x = Foo\rangle$ show ?thesis (proof)   
next case (Bar a) 

from $\langle x = Bar a\rangle$ show ?thesis (proof) qed end 

# 1.5.3 Elimination statements and case-splitting

The consider states rules for generalized elimination and case splitting. This is like a toplevel statement theorem obtains used within a proof body; or like a multi-branch obtain without activation of the local context elements yet. 

The proof method cases is able to use such rules with forward-chaining (e.g. via then). This leads to the subsequent pattern for case-splitting in a particular situation within a proof. 

notepad   
begin   
consider $(a)A\mid (b)B\mid (c)C$ （20 $\langle \mathrm{proof}\rangle$ -typically by auto,by blast etc. then have something   
proof cases case a then show ?thesis $\langle \mathrm{proof}\rangle$ next case $^b$ then show ?thesis $\langle \mathrm{proof}\rangle$ next case $^c$ then show ?thesis $\langle \mathrm{proof}\rangle$ qed   
end 

# 1.5.4 Obtaining local contexts

A single “case” branch may be inlined into Isar proof text via obtain. This proves (Vx. B x =⇒ thesis) =⇒ thesis on the spot, and augments the context afterwards. 

notepad   
begin   
fix $B::$ 'a $\Rightarrow$ bool 

obtain $x$ where $Bx\langle \text{proof}\rangle$ note $\langle Bx\rangle$ 

Conclusions from this context may not mention $x$ again! 

{ obtain $x$ where $Bx\langle \text{proof}\rangle$ from $\langle Bx\rangle$ have $C\langle \text{proof}\rangle$ } note $\langle C\rangle$ end 

# The Isabelle/Isar Framework

Isabelle/Isar [58, 59, 37, 63, 62, 60] is a generic framework for developing formal mathematical documents with full proof checking. Definitions, statements and proofs are organized as theories. A collection of theories sources may be presented as a printed document; see also chapter 4. 

The main concern of Isar is the design of a human-readable structured proof language, which is called the “primary proof format” in Isar terminology. Such a primary proof language is somewhere in the middle between the extremes of primitive proof objects and actual natural language. 

Thus Isar challenges the traditional way of recording informal proofs in mathematical prose, as well as the common tendency to see fully formal proofs directly as objects of some logical calculus (e.g. $\lambda$ -terms in a version of type theory). Technically, Isar is an interpreter of a simple block-structured language for describing the data flow of local facts and goals, interspersed with occasional invocations of proof methods. Everything is reduced to logical inferences internally, but these steps are somewhat marginal compared to the overall bookkeeping of the interpretation process. Thanks to careful design of the syntax and semantics of Isar language elements, a formal record of Isar commands may later appear as an intelligible text to the human reader. 

The Isar proof language has emerged from careful analysis of some inherent virtues of the logical framework Isabelle/Pure [45, 46], notably composition of higher-order natural deduction rules, which is a generalization of Gentzen’s original calculus [18]. The approach of generic inference systems in Pure is continued by Isar towards actual proof texts. See also figure 2.1 

Concrete applications require another intermediate layer: an object-logic. Isabelle/HOL [39] (simply-typed set-theory) is most commonly used; elementary examples are given in the directories ~~/src/Pure/Examples and ~~/ src/HOL/Examples. Some examples demonstrate how to start a fresh objectlogic from Isabelle/Pure, and use Isar proofs from the very start, despite the lack of advanced proof tools at such an early stage (e.g. see ~~/src/Pure/ Examples/Higher_Order_Logic.thy). Isabelle/FOL [42] and Isabelle/ZF [43] also work, but are much less developed. 

Inferences: 

$$
\begin{array}{c c} & \stackrel {{[ A ]}} {{\vdots}} \\ \frac {A \longrightarrow B A}{B} & \frac {B}{A \longrightarrow B} \end{array}
$$

Isabelle/Pure: 

$$
(A \longrightarrow B) \Longrightarrow A \Longrightarrow B \quad (A \Longrightarrow B) \Longrightarrow A \longrightarrow B
$$

Isabelle/Isar: 

have $A \longrightarrow B$ hproof i have $A \longrightarrow B$ also have A hproof i proof finally have $B$ . assume A then show B hproof i qed 

Figure 2.1: Natural Deduction via inferences according to Gentzen, rules in Isabelle/Pure, and proofs in Isabelle/Isar 

In order to illustrate natural deduction in Isar, we shall subsequently refer to the background theory and library of Isabelle/HOL. This includes common notions of predicate logic, naive set-theory etc. using fairly standard mathematical notation. From the perspective of generic natural deduction there is nothing special about the logical connectives of HOL (∧, ∨, ∀ , ∃ , etc.), only the resulting reasoning principles are relevant to the user. There are similar rules available for set-theory operators $( \cap , \cup , \cap , \cup$ , etc.), or any other theory developed in the library (lattice theory, topology etc.). 

Subsequently we briefly review fragments of Isar proof texts corresponding directly to such general deduction schemes. The examples shall refer to settheory, to minimize the danger of understanding connectives of predicate logic as something special. 

The following deduction performs ∩-introduction, working forwards from assumptions towards the conclusion. We give both the Isar text, and depict the primitive rule involved, as determined by unification of fact and goal statements against rules that are declared in the library context. 

assume $x \in A$ and $x \in B$ 

then have $x \in A \cap B$ .. 

$$
\frac {x \in A x \in B}{x \in A \cap B}
$$

Note that assume augments the proof context, then indicates that the cur-

rent fact shall be used in the next step, and have states an intermediate goal. The two dots “..” refer to a complete proof of this claim, using the indicated facts and a canonical rule from the context. We could have been more explicit here by spelling out the final proof step via the by command: 

assume $x \in A$ and $x \in B$ 

then have $x \in A \cap B$ by (rule IntI ) 

The format of the ∩-introduction rule represents the most basic inference, which proceeds from given premises to a conclusion, without any nested proof context involved. 

The next example performs backwards introduction of $\cap A$ , the intersection of all sets within a given set. This requires a nested proof of set membership within a local context, where $A$ is an arbitrary-but-fixed member of the collection: 

have $x \in \cap { \mathcal { A } }$ 

proof 

fix A 

assume $A \in { \mathcal { A } }$ 

show x ∈ A hproof i 

qed 

$\begin{array} { c } { [ A ] [ A \in \mathcal { A } ] } \\ { \vdots } \\ { \frac { x \mathrm { ~ \in ~ } A } { x \mathrm { ~ \in ~ } \bigcap A } } \end{array}$ 

This Isar reasoning pattern again refers to the primitive rule depicted above. The system determines it in the “proof” step, which could have been spelled out more explicitly as “proof (rule InterI )”. Note that the rule involves both a local parameter $A$ and an assumption $A \in { \mathcal { A } }$ in the nested reasoning. Such compound rules typically demands a genuine subproof in Isar, working backwards rather than forwards as seen before. In the proof body we encounter the fix-assume-show outline of nested subproofs that is typical for Isar. The final show is like have followed by an additional refinement of the enclosing claim, using the rule derived from the proof body. 

The next example involves $\cup A$ , which can be characterized as the set of all $x$ such that $\exists A$ . $x \in A \land A \in A$ . The elimination rule for $x \in \cup { \mathcal { A } }$ does not mention $\exists$ and $\wedge$ at all, but admits to obtain directly a local $A$ such that $x \in A$ and $A \in { \mathcal { A } }$ hold. This corresponds to the following Isar proof and inference rule, respectively: 

assume $x\in \bigcup \mathcal{A}$ then have $C$ proof fix $A$ assume $x\in A$ and $A\in \mathcal{A}$ show $C$ (proof)   
qed 

$[A][x\in A,A\in \mathcal{A}]$ $\begin{array}{l}\underline{\underline{x}}\in \bigcup \mathcal{A}\\ \underline{\underline{C}} \end{array}$ 

Although the Isar proof follows the natural deduction rule closely, the text reads not as natural as anticipated. There is a double occurrence of an arbitrary conclusion $C$ , which represents the final result, but is irrelevant for now. This issue arises for any elimination rule involving local parameters. Isar provides the derived language element obtain, which is able to perform the same elimination proof more conveniently: 

assume $x\in \bigcup \mathcal{A}$ thenobtain $A$ where $x\in A$ and $A\in \mathcal{A}$ .. 

Here we avoid to mention the final conclusion $C$ and return to plain forward reasoning. The rule involved in the “..” proof is the same as before. 

# 2.1 The Pure framework

The Pure logic [45, 46] is an intuitionistic fragment of higher-order logic [14]. In type-theoretic parlance, there are three levels of $\lambda$ -calculus with corresponding arrows $\Rightarrow / \Lambda / \Longrightarrow$ : 

$$
\alpha \Rightarrow \beta \quad \text {s y n t a c t i c f u n c t i o n s p a c e (t e r m s d e p e n d i n g o n t e r m s)}
$$

$$
\bigwedge x. B (x) \quad \text {u n i v e r s a l q u a n t i f i c a t i o n (p r o o f s d e p e n d i n g o n t e r m s)}
$$

$$
A \Longrightarrow B \quad \text {i m p l i c a t i o n (p r o o f s d e p e n d i n g o n p r o o f s)}
$$

Here only the types of syntactic terms, and the propositions of proof terms have been shown. The $\lambda$ -structure of proofs can be recorded as an optional feature of the Pure inference kernel [6], but the formal system can never depend on them due to proof irrelevance. 

On top of this most primitive layer of proofs, Pure implements a generic calculus for nested natural deduction rules, similar to [52]. Here object-logic inferences are internalized as formulae over $\Lambda \mathrm { a n d } \Longrightarrow$ . Combining such rule statements may involve higher-order unification [44]. 

# 2.1.1 Primitive inferences

Term syntax provides explicit notation for abstraction $\lambda x : : \alpha$ . $b ( x )$ and application $\textit { b a }$ , while types are usually implicit thanks to type-inference; terms of type prop are called propositions. Logical statements are composed via ${ \textstyle \bigwedge } x : : \alpha . \ B ( x )$ $B ( x )$ and $A \Longrightarrow B$ . Primitive reasoning operates on judgments of the form $\Gamma \vdash \varphi$ , with standard introduction and elimination rules for $\Lambda$ and =⇒ that refer to fixed parameters $x _ { 1 }$ , . . . , $x _ { m }$ and hypotheses $A _ { 1 }$ , . . . , $A _ { n }$ from the context $\Gamma$ ; the corresponding proof terms are left implicit. The subsequent inference rules define $\Gamma \vdash \varphi$ inductively, relative to a collection of axioms from the implicit background theory: 

$$
\begin{array}{l} \begin{array}{c c} \frac {A \text {i s a x i o m}}{\vdash A} & \overline {{A \vdash A}} \end{array} \\ \frac {\Gamma \vdash B (x) \quad x \notin \Gamma}{\Gamma \vdash \bigwedge x . B (x)} \qquad \frac {\Gamma \vdash \bigwedge x . B (x)}{\Gamma \vdash B (a)} \\ \frac {\Gamma \vdash B}{\Gamma - A \vdash A \Rightarrow B} \quad \frac {\Gamma_ {1} \vdash A \Longrightarrow B \quad \Gamma_ {2} \vdash A}{\Gamma_ {1} \cup \Gamma_ {2} \vdash B} \\ \end{array}
$$

Furthermore, Pure provides a built-in equality ≡ :: $\alpha \Rightarrow \alpha \Rightarrow p r o p$ with axioms for reflexivity, substitution, extensionality, and $\alpha \beta \eta$ -conversion on $\lambda$ -terms. 

An object-logic introduces another layer on top of Pure, e.g. with types $i$ for individuals and $o$ for propositions, term constants Trueprop :: $o \Rightarrow p r o p$ as (implicit) derivability judgment and connectives like $\bigwedge ~ \{ : ~ o \Rightarrow ~ o \Rightarrow ~ o$ or $\forall ~ \colon ( i \Rightarrow o ) \Rightarrow o$ , and axioms for object-level rules such as conjI : $A \implies$ $B \implies A \land B$ or allI : $( \land x . \ B \ x ) \implies \forall x$ . B $x$ . Derived object rules are represented as theorems of Pure. After the initial object-logic setup, further axiomatizations are usually avoided: definitional principles are used instead (e.g. definition, inductive, fun, function). 

# 2.1.2 Reasoning with rules

Primitive inferences mostly serve foundational purposes. The main reasoning mechanisms of Pure operate on nested natural deduction rules expressed 

as formulae, using $\Lambda$ to bind local parameters and =⇒ to express entailment. Multiple parameters and premises are represented by repeating these connectives in a right-associative manner. 

Thanks to the Pure theorem $' A \implies ( / x . ~ B ~ x ) ) \equiv ( / \Lambda x . ~ A \implies B ~ x )$ $x$ the connectives $\Lambda$ and =⇒ commute. So we may assume w.l.o.g. that rule statements always observe the normal form where quantifiers are pulled in front of implications at each level of nesting. This means that any Pure proposition may be presented as a Hereditary Harrop Formula [33] which is of the form Vx 1 . . . $x _ { m }$ . ${ \cal H } _ { 1 } \Longrightarrow . .$ . $H _ { n } \implies A$ for $m$ , $n \geq 0$ , and $A$ atomic, and $H _ { 1 }$ , . . . , $H _ { n }$ being recursively of the same format. Following the convention that outermost quantifiers are implicit, Horn clauses $A _ { 1 } \Longrightarrow . . .$ $A _ { n } \Longrightarrow A$ are a special case of this. 

For example, the $\lceil \rceil .$ -introduction rule encountered before is represented as a Pure theorem as follows: 

$$
I n t I \colon x \in A \Longrightarrow x \in B \Longrightarrow x \in A \cap B
$$

This is a plain Horn clause, since no further nesting on the left is involved. The general $\cap$ -introduction corresponds to a Hereditary Harrop Formula with one additional level of nesting: 

$$
I n t e r I \colon (\bigwedge A. A \in \mathcal {A} \Longrightarrow x \in A) \Longrightarrow x \in \bigcap \mathcal {A}
$$

Goals are also represented as rules: $A _ { 1 } \Longrightarrow . . .$ $A _ { n } \implies C$ states that the subgoals $A _ { 1 }$ , . . . , $A _ { n }$ entail the result $C$ ; for $n = 0$ the goal is finished. To allow $C$ being a rule statement itself, there is an internal protective marker $\# : : p r o p \Rightarrow p r o p$ , which is defined as identity and hidden from the user. We initialize and finish goal states as follows: 

$$
\overline {{C \Rightarrow \# C}} (i n i t) \quad \frac {\# C}{C} (f i n i s h)
$$

Goal states are refined in intermediate proof steps until a finished form is achieved. Here the two main reasoning principles are resolution, for backchaining a rule against a subgoal (replacing it by zero or more subgoals), and assumption, for solving a subgoal (finding a short-circuit with local assumptions). Below $\textstyle { \overline { { x } } }$ stands for $x _ { 1 }$ , . . . , $x _ { n }$ (for $n \geq 0$ ). 

$$
\begin{array}{l} r u l e: \quad \bar {A} \bar {a} \Longrightarrow B \bar {a} \\ \text {g o a l :} \quad (\bigwedge \bar {x}. \bar {H} \bar {x} \Longrightarrow B ^ {\prime} \bar {x}) \Longrightarrow C \\ \begin{array}{c} \text {g o a l u n i f i e r :} \quad (\lambda \overline {{x}}. B (\overline {{a}} \overline {{x}})) \theta = B ^ {\prime} \theta \\ \hline (\bigwedge \overline {{x}}. \overline {{H}} \overline {{x}} \Longrightarrow \overline {{A}} (\overline {{a}} \overline {{x}})) \theta \Longrightarrow C \theta \end{array} (r e s o l u t i o n) \\ \end{array}
$$

$$
\begin{array}{r l} & g o a l: (\bigwedge \overline {{x}}. \overline {{H}} \overline {{x}} \Longrightarrow A \overline {{x}}) \Longrightarrow C \\ & a s s m u n i f i e r: A \theta = H _ {i} \theta \mathrm {f o r s o m e} H _ {i} \\ & \hline C \theta (a s s u m p t i o n) \end{array}
$$

The following trace illustrates goal-oriented reasoning in Isabelle/Pure: 

$$
\begin{array}{l} (A \wedge B \Longrightarrow B \wedge A) \Longrightarrow \# (A \wedge B \Longrightarrow B \wedge A) \quad (i n i t) \\ (A \wedge B \Longrightarrow B) \Longrightarrow (A \wedge B \Longrightarrow A) \Longrightarrow \# \dots \quad (\text {r e s o l u t i o n} B \Longrightarrow A \Longrightarrow B \wedge A) \\ (A \wedge B \Longrightarrow A \wedge B) \Longrightarrow (A \wedge B \Longrightarrow A) \Longrightarrow \# \dots \quad (\text {r e s o l u t i o n} A \wedge B \Longrightarrow B) \\ (A \wedge B \Longrightarrow A) \Longrightarrow \# \dots \quad (a s s u m p t i o n) \\ (A \wedge B \Longrightarrow A \wedge B) \Longrightarrow \# \dots \quad (r e s o l u t i o n A \wedge B \Longrightarrow A) \\ \# \dots \quad (a s s u m p t i o n) \\ A \wedge B \Longrightarrow B \wedge A \quad (f i n i s h) \\ \end{array}
$$

Compositions of assumption after resolution occurs quite often, typically in elimination steps. Traditional Isabelle tactics accommodate this by a combined elim_resolution principle. In contrast, Isar uses a combined refinement rule as follows:1 

$$
\text {s u b g o a l :} \quad (\wedge \bar {x}. \bar {H} \bar {x} \Longrightarrow B ^ {\prime} \bar {x}) \Longrightarrow C
$$

$$
s u b p r o o f: \quad \bar {G} \bar {a} \Longrightarrow B \bar {a} \quad \text {f o r s c h e m a t i c} \bar {a}
$$

$$
\text {c o n c l u n i f i e r :} \quad (\lambda \bar {x}. B (\bar {a} \bar {x})) \theta = B ^ {\prime} \theta
$$

$$
\frac {\text {a s s m u n i f i e r s :} \quad (\lambda \overline {{x}} . G _ {j} (\overline {{a}} \overline {{x}})) \theta = H _ {i} \theta \quad \text {f o r e a c h G _ {j} s o m e H _ {i}}}{C \theta} (r e f i n e m e n t)
$$

Here the subproof rule stems from the main fix-assume-show outline of Isar (cf. §2.2.3): each assumption indicated in the text results in a marked premise $G$ above. Consequently, fix-assume-show enables to fit the result of a subproof quite robustly into a pending subgoal, while maintaining a good measure of flexibility: the subproof only needs to fit modulo unification, and its assumptions may be a proper subset of the subgoal premises (see §2.2.3). 

# 2.2 The Isar proof language

Structured proofs are presented as high-level expressions for composing entities of Pure (propositions, facts, and goals). The Isar proof language allows 

to organize reasoning within the underlying rule calculus of Pure, but Isar is not another logical calculus. Isar merely imposes certain structure and policies on Pure inferences. The main grammar of the Isar proof language is given in figure 2.2. 

The construction of the Isar proof language proceeds in a bottom-up fashion, as an exercise in purity and minimalism. The grammar in appendix A.1.1 describes the primitive parts of the core language (category proof ), which is embedded into the main outer theory syntax via elements that require a proof (e.g. theorem, lemma, function, termination). 

The syntax for terms and propositions is inherited from Pure (and the objectlogic). A pattern is a term with schematic variables, to be bound by higherorder matching. Simultaneous propositions or facts may be separated by the and keyword. 

Facts may be referenced by name or proposition. For example, the result of “have a: A hproof i” becomes accessible both via the name $a$ and the literal proposition ‹A›. Moreover, fact expressions may involve attributes that modify either the theorem or the background context. For example, the expression “a [OF b]” refers to the composition of two facts according to the resolution inference of §2.1.2, while “ $a$ [intro]” declares a fact as introduction rule in the context. 

The special fact called “this” always refers to the last result, as produced by note, assume, have, or show. Since note occurs frequently together with then, there are some abbreviations: 

from a ≡ note a then 

with a ≡ from a and this 

The method category is essentially a parameter of the Isar language and may be populated later. The command method_setup allows to define proof methods semantically in Isabelle/ML. The Eisbach language allows to define proof methods symbolically, as recursive expressions over existing methods [32]; see also ~~/src/HOL/Eisbach. 

Methods use the facts indicated by then or using, and then operate on the goal state. Some basic methods are predefined in Pure: “−” leaves the goal unchanged, “this” applies the facts as rules to the goal, “rule” applies the facts to another rule and the result to the goal (both “this” and “rule” refer to resolution of §2.1.2). The secondary arguments to “rule” may be specified explicitly as in $^ { * } ( r u l e \ a ) ^ { * }$ , or picked from the context. In the latter case, the system first tries rules declared as elim or dest, followed by those declared as intro. 

The default method for proof is “standard” (which subsumes rule with arguments picked from the context), for qed it is “succeed”. Further abbreviations for terminal proof steps are “by method1 method2” for “proof method1 qed method2”, and “..” for “by standard, and “.” for “by this”. The command “unfolding facts” operates directly on the goal by applying equalities. 

Block structure can be indicated explicitly by $\cdots \ r ^ { \mathscr { G } }$ , although the body of a subproof “proof . . . qed” already provides implicit nesting. In both situations, next jumps into the next section of a block, i.e. it acts like closing an implicit block scope and opening another one. There is no direct connection to subgoals here! 

The commands fix and assume build up a local context (see §2.2.1), while show refines a pending subgoal by the rule resulting from a nested subproof (see §2.2.3). Further derived concepts will support calculational reasoning (see §2.2.4). 

# 2.2.1 Context elements

In judgments $\Gamma \vdash \varphi$ of the primitive framework, $\Gamma$ essentially acts like a proof context. Isar elaborates this idea towards a more advanced concept, with additional information for type-inference, term abbreviations, local facts, hypotheses etc. 

The element fix $x \because \alpha$ declares a local parameter, i.e. an arbitrary-but-fixed entity of a given type; in results exported from the context, $x$ may become anything. The assume «inference» element provides a general interface to hypotheses: assume «inference» $A$ produces $A \vdash A$ locally, while the included inference tells how to discharge $A$ from results $A \vdash B$ later on. There is no surface syntax for «inference», i.e. it may only occur internally when derived commands are defined in ML. 

The default inference for assume is export as given below. The derived element define $x$ where $x = a$ is defined as fix $x$ assume «expand» $x = a$ , with the subsequent inference expand. 

$$
\frac {\Gamma \vdash B}{\Gamma - A \vdash A \Longrightarrow B} (e x p o r t) \qquad \frac {\Gamma \vdash B x}{\Gamma - (x \equiv a) \vdash B a} (e x p a n d)
$$

The most interesting derived context element in Isar is obtain [59, §5.3], which supports generalized elimination steps in a purely forward manner. The obtain command takes a specification of parameters $x$ and assumptions 

$\overline { { A } }$ to be added to the context, together with a proof of a case rule stating that this extension is conservative (i.e. may be removed from closed results later on): 

$\langle \text{facts} \rangle$ obtain $\overline{x}$ where $\overline{A} \overline{x}$ $\langle \text{proof} \rangle \equiv$ 

have case: $\Lambda$ thesis. $(\bigwedge \overline{x}. \overline{A} \overline{x} \Rightarrow \text{thesis}) \Rightarrow \text{thesis}$ 

```txt
proof - 
```

```txt
fixthesis 
```

assume [intro]: $\bigwedge \overline{x}$ $\overline{A}\overline{x}\Rightarrow$ thesis 

```txt
showthesis using <facts> <proof> 
```

```txt
qed 
```

fix $\overline{x}$ assume «elimination case» $\overline{A} \overline{x}$ 

case: $\Gamma \vdash \bigwedge$ thesis. $(\bigwedge \overline{x}. \overline{A} \overline{x} \Rightarrow \text{thesis}) \Rightarrow \text{thesis}$ 

result: $\Gamma \cup \overline{A}\overline{y}\vdash B$ (elimination) 

Here the name “thesis” is a specific convention for an arbitrary-but-fixed proposition; in the primitive natural deduction rules shown before we have occasionally used $ { C }$ . The whole statement of “obtain $x$ where $\textit { A } \boldsymbol { x } ^ { \prime \prime }$ can be read as a claim that $A$ $x$ may be assumed for some arbitrary-but-fixed $x$ . Also note that “obtain $A$ and B” without parameters is similar to “have $A$ and $B ^ { \ast }$ , but the latter involves multiple subgoals that need to be proven separately. 

The subsequent Isar proof texts explain all context elements introduced above using the formal proof language itself. After finishing a local proof within a block, the exported result is indicated via note. 

{ fix x assume A have B $x$ <proof> have B <proof>   
}   
note $\langle \bigwedge x.Bx\rangle$ note $\langle A\Rightarrow B\rangle$ { define $x$ where $x\equiv a$ obtain $x$ where $A\times$ <proof> have B <proof>   
}   
note $<  Ba>$ note $<  B>$ 

This explains the meaning of Isar context elements without, without goal states getting in the way. 

# 2.2.2 Structured statements

The syntax of top-level theorem statements is defined as follows: 

statement $\equiv$ name: props and ... context* conclusion   
context $\equiv$ fixes vars and ... assumes name: props and ..   
conclusion $\equiv$ shows name: props and .. obtains props and... where name: props and ... 

A simple statement consists of named propositions. The full form admits local context elements followed by the actual conclusions, such as “fixes $x$ assumes A x shows $\textit { B x }$ ”. The final result emerges as a Pure rule after discharging the context: $\Lambda x$ . A $x \Longrightarrow B x$ . 

The obtains variant is another abbreviation defined below; unlike obtain (cf. $\ S 2 . 2 . 1 )$ there may be several “cases” separated by “ ”, each consisting of several parameters (vars) and several premises (props). This specifies multibranch elimination rules. 

obtains $\overline{x}$ where $\overline{A}\overline{x}|\ldots\equiv$ fixes thesis  
assumes [intro]: $\bigwedge \overline{x}$ . $\overline{A}\overline{x}\Rightarrow$ thesis and  
shows thesis 

Presenting structured statements in such an “open” format usually simplifies the subsequent proof, because the outer structure of the problem is already laid out directly. E.g. consider the following canonical patterns for shows and obtains, respectively: 

theorem  
fixes $x$ and $y$ assumes $A$ and $B$ shows $C$ proof -  
from $\langle A x\rangle$ and $\langle B y\rangle$ show $C$ qed 

Here local facts $\langle A  { x } \rangle$ and $\langle B \ y \rangle$ are referenced immediately; there is no need to decompose the logical rule structure again. In the second proof the final “then show thesis ..” involves the local rule case $\bigwedge { x \ y . \ A \ x } \implies B \ y \implies$ thesis for the particular instance of terms $a$ and $b$ produced in the body. 

# 2.2.3 Structured proof refinement

By breaking up the grammar for the Isar proof language, we may understand a proof text as a linear sequence of individual proof commands. These are interpreted as transitions of the Isar virtual machine (Isar/VM), which operates on a block-structured configuration in single steps. This allows users to write proof texts in an incremental manner, and inspect intermediate configurations for debugging. 

The basic idea is analogous to evaluating algebraic expressions on a stack machine: $( a + b ) \cdot c$ then corresponds to a sequence of single transitions for each symbol $( , \ a , + , \ b , \ )$ , ·, $c$ . In Isar the algebraic values are facts or goals, and the operations are inferences. 

The Isar/VM state maintains a stack of nodes, each node contains the local proof context, the linguistic mode, and a pending goal (optional). The mode determines the type of transition that may be performed next, it essentially alternates between forward and backward reasoning, with an intermediate stage for chained facts (see figure 2.3). 

For example, in state mode Isar acts like a mathematical scratch-pad, accepting declarations like fix, assume, and claims like have, show. A goal statement changes the mode to prove, which means that we may now refine the problem via unfolding or proof. Then we are again in state mode of a proof body, which may issue show statements to solve pending subgoals. A concluding qed will return to the original state mode one level upwards. The subsequent Isar/VM trace indicates block structure, linguistic mode, goal state, and inferences: 

have $A\longrightarrow B$ begin prove $(A\longrightarrow B)\Rightarrow \# (A\longrightarrow B)$ (init)   
proof state $(A\Rightarrow B)\Rightarrow \# (A\longrightarrow B)$ (resolution impI)   
assume $A$ state   
show $B$ begin prove   
(proofo) end state #(A→B) (refinement #A→B)   
qed end state $A\longrightarrow B$ (finish) 

Here the refinement inference from §2.1.2 mediates composition of Isar subproofs nicely. Observe that this principle incorporates some degree of freedom in proof composition. In particular, the proof body allows parameters and assumptions to be re-ordered, or commuted according to Hereditary Harrop Form. Moreover, context elements that are not used in a subproof may be omitted altogether. For example: 

have $\wedge x y$ $A x\Rightarrow B y\Rightarrow C x y$ have $\wedge x y$ $A x\Rightarrow B y\Rightarrow C x y$ proof - proof - fix $x$ and $y$ fix $x$ assume $A x$ assume $A x$ and $B y$ fix $y$ assume $B y$ show $C x y$ (proof) show $C x y$ (proof)   
qed qed   
have $\wedge x y$ $A x\Rightarrow B y\Rightarrow C x y$ have $\wedge x y$ $A x\Rightarrow B y\Rightarrow C x y$ proof - proof - fix $y$ assume $B y$ fix $y$ assume $B y$ fix $x$ assume $A x$ show $C x y$ (proof) show $C x y$ (proof)   
qed qed 

Such fine-tuning of Isar text is practically important to improve readability. Contexts elements are rearranged according to the natural flow of reasoning in the body, while still observing the overall scoping rules. 

This illustrates the basic idea of structured proof processing in Isar. The main mechanisms are based on natural deduction rule composition within the Pure framework. In particular, there are no direct operations on goal states within the proof body. Moreover, there is no hidden automated reasoning involved, just plain unification. 

# 2.2.4 Calculational reasoning

The existing Isar infrastructure is sufficiently flexible to support calculational reasoning (chains of transitivity steps) as derived concept. The generic proof elements introduced below depend on rules declared as trans in the context. It is left to the object-logic to provide a suitable rule collection for mixed relations of =, $<$ , $\leq$ , $\subset$ , $\subseteq$ etc. Due to the flexibility of rule composition (§2.1.2), substitution of equals by equals is covered as well, even substitution of inequalities involving monotonicity conditions; see also [59, §6] and [5]. 

The generic calculational mechanism is based on the observation that rules such as trans: $x = y \implies y = z \implies x = z$ proceed from the premises towards the conclusion in a deterministic fashion. Thus we may reason in forward mode, feeding intermediate results into rules selected from the context. The course of reasoning is organized by maintaining a secondary fact called “calculation”, apart from the primary “this” already provided by the Isar primitives. In the definitions below, $O F$ refers to resolution (§2.1.2) with multiple rule arguments, and trans represents to a suitable rule from the context: 

also $_ 0$ ≡ note calculation = this 

alson+1 ≡ note calculation = trans [OF calculation this] 

finally ≡ also from calculation 

The start of a calculation is determined implicitly in the text: here also sets calculation to the current result; any subsequent occurrence will update calculation by combination with the next result and a transitivity rule. The calculational sequence is concluded via finally, where the final result is exposed for use in a concluding claim. 

Here is a canonical proof pattern, using have to establish the intermediate results: 

have $a = b$ hproof i 

also have . . . = c hproof i 

also have . . . = d hproof i 

finally have $a = d$ . 

The term “. . . ” (literal ellipsis) is a special abbreviation provided by the Isabelle/Isar term syntax: it statically refers to the right-hand side argument of the previous statement given in the text. Thus it happens to coincide with relevant sub-expressions in the calculational chain, but the exact correspondence is dependent on the transitivity rules being involved. 

Symmetry rules such as $x = y \Longrightarrow y = x$ are like transitivities with only one premise. Isar maintains a separate rule collection declared via the sym attribute, to be used in fact expressions “ $a$ [symmetric]”, or single-step proofs “assume $x = y$ then have $y = x$ ..”. 

# 2.3 Example: First-Order Logic

theory First_Order_Logic 

imports Base 

begin 

In order to commence a new object-logic within Isabelle/Pure we introduce abstract syntactic categories $i$ for individuals and $o$ for object-propositions. The latter is embedded into the language of Pure propositions by means of a separate judgment. 

typedecl $i$ 

typedecl o 

judgment Trueprop :: o ⇒ prop (_ 5) 

Note that the object-logic judgment is implicit in the syntax: writing $A$ produces Trueprop A internally. From the Pure perspective this means “ $A$ is derivable in the object-logic”. 

# 2.3.1 Equational reasoning

Equality is axiomatized as a binary predicate on individuals, with reflexivity as introduction, and substitution as elimination principle. Note that the latter is particularly convenient in a framework like Isabelle, because syntactic congruences are implicitly produced by unification of $B$ $x$ against expressions containing occurrences of $x$ . 

axiomatization equal :: $i \Rightarrow i \Rightarrow o$ (infix = 50) 

where refl [intro]: $x = x$ 

and subst [elim]: $x = y \Longrightarrow B x \Longrightarrow B y$ $y$ 

Substitution is very powerful, but also hard to control in full generality. We derive some common symmetry / transitivity schemes of equal as particular consequences. 

theorem sym [sym]: 

assumes $x = y$ 

shows $y = x$ 

proof − 

have $x = x$ .. 

with $x = y \rangle$ show $y = x$ .. 

qed 

theorem forw_subst [trans]: 

assumes $y = x$ and $\textit { B x }$ 

shows B y 

proof − 

from $\langle y = x \rangle$ › have $x = y$ .. 

from this and $\textit { \textbf { ‰} }$ show B y .. 

qed 

theorem back_subst [trans]: 

assumes $\textit { B x }$ and $x = y$ 

shows B y 

proof − 

from $\langle x = y \rangle$ › and $\textit { \textbf { ‰} }$ 

show $By$ .  
qed  
theorem trans [trans]: assumes $x = y$ and $y = z$ shows $x = z$ proof - from $\langle y = z\rangle$ and $\langle x = y\rangle$ show $x = z$ .  
qed 

# 2.3.2 Basic group theory

As an example for equational reasoning we consider some bits of group theory. The subsequent locale definition postulates group operations and axioms; we also derive some consequences of this specification. 

locale group =  
fixes prod :: $i \Rightarrow i \Rightarrow i$ (infix o 70)  
and inv :: $i \Rightarrow i$ ((\_^{-1}) [1000] 999)  
and unit :: $i$ (1)  
assumes assoc: $(x \circ y) \circ z = x \circ (y \circ z)$ and left_unit: $1 \circ x = x$ and left_inv: $x^{-1} \circ x = 1$ begin 

theorem right_inv: $x\circ x^{-1} = 1$ proof - have $x\circ x^{-1} = 1\circ (x\circ x^{-1})$ by (rule left_unit [symmetric]) also have $\dots = (1\circ x)\circ x^{-1}$ by (rule assoc [symmetric]) also have $1 = (x^{-1})^{-1}\circ x^{-1}$ by (rule left_inv [symmetric]) also have $\dots \circ x = (x^{-1})^{-1}\circ (x^{-1}\circ x)$ by (rule assoc) also have $x^{-1}\circ x = 1$ by (rule left_inv) also have $((x^{-1})^{-1}\circ \ldots)\circ x^{-1} = (x^{-1})^{-1}\circ (1\circ x^{-1})$ by (rule assoc) also have $1\circ x^{-1} = x^{-1}$ by (rule left_unit) also have $(x^{-1})^{-1}\circ \ldots = 1$ by (rule left_inv) finally show $x\circ x^{-1} = 1$ .   
qed 

theorem right_unit: $x\circ 1 = x$ proof - have $1 = x^{-1}\circ x$ by (rule left_inv [symmetric]) also have $x\circ \ldots = (x\circ x^{-1})\circ x$ by (rule assoc [symmetric]) also have $x\circ x^{-1} = 1$ by (rule right_inv) 

also have . . . ◦ x = x by (rule left_unit) 

finally show $x \circ 1 = x$ . 

qed 

Reasoning from basic axioms is often tedious. Our proofs work by producing various instances of the given rules (potentially the symmetric form) using the pattern “have eq by (rule r)” and composing the chain of results via also/finally. These steps may involve any of the transitivity rules declared in §2.3.1, namely trans in combining the first two results in right_inv and in the final steps of both proofs, forw_subst in the first combination of right_unit, and back_subst in all other calculational steps. 

Occasional substitutions in calculations are adequate, but should not be overemphasized. The other extreme is to compose a chain by plain transitivity only, with replacements occurring always in topmost position. For example: 

have $x \circ 1 = x \circ ( x ^ { - 1 } \circ x )$ unfolding left_inv .. 

also have $\dots = ( x \circ x ^ { - 1 } ) \circ x$ unfolding assoc .. 

also have $\dots = 1 \circ x$ unfolding right_inv .. 

also have $\dots = x$ unfolding left_unit .. 

finally have $x \circ 1 = x$ . 

Here we have re-used the built-in mechanism for unfolding definitions in order to normalize each equational problem. A more realistic object-logic would include proper setup for the Simplifier (§9.3), the main automated tool for equational reasoning in Isabelle. Then “unfolding left_inv ..” would become “by (simp only: left_inv)” etc. 

end 

# 2.3.3 Propositional logic

We axiomatize basic connectives of propositional logic: implication, disjunction, and conjunction. The associated rules are modeled after Gentzen’s system of Natural Deduction [18]. 

axiomatization imp :: o ⇒ o ⇒ o (infixr −→ 25) 

where impI [intro]: $( A \implies B ) \implies A \longrightarrow B$ 

and impD [dest]: (A −→ B) =⇒ A =⇒ B 

axiomatization disj :: o ⇒ o ⇒ o (infixr ∨ 30) 

where disjI 1 [intro]: $A \Longrightarrow A \lor B$ 

and disjI 2 [intro]: $B \Longrightarrow A \lor B$ 

and disjE [elim]: A ∨ B =⇒ (A =⇒ C ) =⇒ (B =⇒ C ) =⇒ C 

axiomatization conj :: o ⇒ o ⇒ o (infixr ∧ 35) 

where conjI [intro]: $A \implies B \implies A \land B$ 

and conjD1: $A \land B \implies A$ 

and conjD2: $A \land B \implies B$ 

The conjunctive destructions have the disadvantage that decomposing $A \land B$ involves an immediate decision which component should be projected. The more convenient simultaneous elimination $A \land B \implies$ ( $A \implies B \implies C ) \implies$ $C$ can be derived as follows: 

theorem conjE [elim]: 

assumes $A \land B$ 

obtains $A$ and $B$ 

proof 

from $\langle A \land B \rangle$ show A by (rule conjD1) 

from $\langle A \land B \rangle$ show $B$ by (rule conjD2) 

qed 

Here is an example of swapping conjuncts with a single intermediate elimination step: 

assume $A \land B$ 

then obtain $B$ and $A$ .. 

then have $B \wedge A$ .. 

Note that the analogous elimination rule for disjunction “assumes A ∨ B obtains $A \ | \ B ^ { \prime } \rangle$ coincides with the original axiomatization of disjE. 

We continue propositional logic by introducing absurdity with its characteristic elimination. Plain truth may then be defined as a proposition that is trivially true. 

axiomatization false :: o (⊥) 

where falseE [elim]: $\bot \implies A$ 

definition true :: o (>) 

where $\top \equiv \bot \longrightarrow \bot$ 

theorem trueI [intro]: > 

unfolding true_def .. 

Now negation represents an implication towards absurdity: 

definition not :: $o \Rightarrow o$ (¬ _ [40] 40) 

where $\lnot \ A \equiv A \longrightarrow \perp$ 

theorem notI [intro]: 

assumes $A\Rightarrow \bot$ shows $\neg A$ unfolding not_def   
proof assume $A$ then show $\perp$ by (rule $\langle A\Rightarrow \bot \rangle$ qed   
theorem notE [elim]: assumes $\neg A$ and $A$ shows $B$ proof - from $\langle \neg A\rangle$ have $A\longrightarrow \bot$ unfolding not_def . from $\langle A\longrightarrow \bot \rangle$ and $\langle A\rangle$ have $\perp$ .. then show $B\ldots$ qed 

# 2.3.4 Classical logic

Subsequently we state the principle of classical contradiction as a local assumption. Thus we refrain from forcing the object-logic into the classical perspective. Within that context, we may derive well-known consequences of the classical principle. 

locale classical $=$ assumes classical: $(\neg C\Rightarrow C)\Rightarrow C$ begin 

theorem double_negation: assumes $\neg \neg C$ shows $C$ proof (rule classical) assume $\neg C$ with $\langle \neg \neg C\rangle$ show $C$ . 

theorem tertium_non_datur: $C \vee \neg C$ proof (rule double_negation)  
show $\neg \neg (C \lor \neg C)$ proof  
assume $\neg (C \lor \neg C)$ have $\neg C$ proof 

assume $C$ then have $C \vee \neg C$ . with $\langle \neg (C \vee \neg C) \rangle$ show $\perp$ . qed  
then have $C \vee \neg C$ .  
with $\langle \neg (C \vee \neg C) \rangle$ show $\perp$ . qed  
qed 

These examples illustrate both classical reasoning and non-trivial propositional proofs in general. All three rules characterize classical logic independently, but the original rule is already the most convenient to use, because it leaves the conclusion unchanged. Note that $( \lnot \ C \Longrightarrow C ) \Longrightarrow C$ fits again into our format for eliminations, despite the additional twist that the context refers to the main conclusion. So we may write classical as the Isar statement “obtains ¬ thesis”. This also explains nicely how classical reasoning really works: whatever the main thesis might be, we may always assume its negation! 

end 

# 2.3.5 Quantifiers

Representing quantifiers is easy, thanks to the higher-order nature of the underlying framework. According to the well-known technique introduced by Church [14], quantifiers are operators on predicates, which are syntactically represented as $\lambda$ -terms of type $i \Rightarrow o$ . Binder notation turns All (λx. B x) into $\forall x$ . B x etc. 

axiomatization All :: $(i\Rightarrow o)\Rightarrow o$ (binder $\forall 10$ where allI [intro]: $(\bigwedge x.Bx)\Longrightarrow \forall x.Bx$ and allD [dest]: $(\forall x.Bx)\Longrightarrow Ba$ 

axiomatization $Ex::(i\Rightarrow o)\Rightarrow o$ (binder $\exists 10$ where exI [intro]: $B a\Longrightarrow (\exists x.Bx)$ and exE [elim]: $(\exists x.Bx)\Longrightarrow (\bigwedge x.Bx\Longrightarrow C)\Longrightarrow C$ 

The statement of $e x E$ corresponds to “assumes $\exists x$ . B x obtains $x$ where $\textit { B x } '$ in Isar. In the subsequent example we illustrate quantifier reasoning involving all four rules: 

theorem assumes $\exists x.\forall y.Rx y$ shows $\forall y.\exists x.Rx y$ proof -V introduction obtain $x$ where $\forall y.Rx y$ using $\langle \exists x.\forall y.Rx y\rangle \ldots$ 1 -e elimination 

fix $y$ have R x y using ‹∀ y. R x y› .. — ∀ destruction then show ∃ x. R x y .. — ∃ introduction qed 

# 2.3.6 Canonical reasoning patterns

The main rules of first-order predicate logic from §2.3.3 and §2.3.5 can now be summarized as follows, using the native Isar statement format of §2.2.2. 

impI : assumes $A \Longrightarrow B$ shows $A \longrightarrow B$ 

impD: assumes $A \longrightarrow B$ and $A$ shows $B$ 

disjI 1: assumes $A$ shows $A \lor B$ 

disjI 2: assumes $B$ shows $A \lor B$ 

disjE: assumes $A \lor B$ obtains $A \mid B$ 

conjI : assumes $A$ and $B$ shows $A \land B$ 

conjE: assumes $A \land B$ obtains $A$ and $B$ 

falseE: assumes $\perp$ shows $A$ 

trueI : shows > 

notI : assumes $A \Longrightarrow \perp$ shows ¬ A 

notE: assumes $\lnot \ A$ and $A$ shows $B$ 

allI : assumes $\Lambda x$ . B x shows ∀ x. B x 

allE: assumes ∀ x. B x shows B a 

exI : assumes B a shows ∃ x. B x 

$e x E$ : assumes ∃ x. B x obtains $a$ where B a 

This essentially provides a declarative reading of Pure rules as Isar reasoning patterns: the rule statements tells how a canonical proof outline shall look like. Since the above rules have already been declared as intro, elim, dest — each according to its particular shape — we can immediately write Isar proof texts as follows: 

have $A \longrightarrow B$ 

proof 

assume A 

show B hproof i 

qed 

have $A \longrightarrow B$ and A hproof i 

then have $B$ .. 

```txt
have A <proof> have A V B <proof> then have A V B .. then have C proof   
have B <proof> assume A then show C <proof> next assume B then show C <proof> qed 
```

have A and B (proof) have A A B (proof) then have A A B .. then obtain A and B .. have $\perp$ (proof) have T .. then have A .. 

have $\neg A$ have $\neg A$ and $A\langle \text{proof}\rangle$ proof then have $B\ldots$ assume $A$ then show $\perp$ (proof)   
qed 

have $\forall x.Bx$ have $\forall x.Bx\langle \text{proof}\rangle$ proof then have $B a..$ fix $x$ show $Bx\langle \mathrm{proof}\rangle$ qed 

have $\exists x$ .Bx have $\exists x$ .Bx (proof)   
proof then obtain a where $B a\ldots$ show $B a\langle \text{proof}\rangle$ qed 

Of course, these proofs are merely examples. As sketched in $\ S 2 . 2 . 3$ , there is a fair amount of flexibility in expressing Pure deductions in Isar. Here the user is asked to express himself adequately, aiming at proof texts of literary quality. 

end 

main $=$ notepad begin statement\* end theorem name: props if name: props for vars theorem name: fixes vars assumes name: props shows name: props proof theorem name: fixes vars assumes name: props obtains (name) clause | ... proof   
proof $=$ refinement\* proper\_proof refinement $\equiv$ apply method supply name $=$ thms subgoal premises name for vars proof using thms unfolding thms   
proper\_proof $=$ proof method? statement\* qed method? by method method | .. | . | sorry | done statement $\equiv$ {statement\*} | next note name $=$ thms let term $=$ term write name (mixfix) fix vars assume name: props if props for vars presume name: props if props for vars define clause case name: case then? goal from thms goal with thms goal also finally goal moreover ultimately goal   
goal $=$ have name: props if name: props for vars proof show name: props if name: props for vars proof show name: props when name: props for vars proof consider (name) clause | ... proof obtain (name) clause proof clause $=$ vars where name: props if props for vars 

Figure 2.2: Main grammar of the Isar proof language 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/94ba2a497c836f4abd9ca9763b07f6b42e1081057b5860bc572e02441dd49e92.jpg)



Figure 2.3: Isar/VM modes


# Part II

# General Language Elements

# Outer syntax — the theory language

The rather generic framework of Isabelle/Isar syntax emerges from three main syntactic categories: commands of the top-level Isar engine (covering theory and proof elements), methods for general goal refinements (analogous to traditional “tactics”), and attributes for operations on facts (within a certain context). Subsequently we give a reference of basic syntactic entities underlying Isabelle/Isar syntax in a bottom-up manner. Concrete theory and proof language elements will be introduced later on. 

In order to get started with writing well-formed Isabelle/Isar documents, the most important aspect to be noted is the difference of inner versus outer syntax. Inner syntax is that of Isabelle types and terms of the logic, while outer syntax is that of Isabelle/Isar theory sources (specifications and proofs). As a general rule, inner syntax entities may occur only as atomic entities within outer syntax. For example, the string $\ " { } \mathbb { X } \ + \ \ y \ "$ and identifier $_ { z }$ are legal term specifications within a theory, while x + y without quotes is not. Printed theory documents usually omit quotes to gain readability (this is a matter of LATEX macro setup, say via \isabellestyle, see also [54]). Experienced users of Isabelle/Isar may easily reconstruct the lost technical information, while mere readers need not care about quotes at all. 

# 3.1 Commands

print_commands∗ : any → 

help∗ : any → 

help 

name 

print_commands prints all outer syntax keywords and commands. 

help pats retrieves outer syntax commands according to the specified name patterns. 

# Examples

Some common diagnostic commands are retrieved like this (according to usual naming conventions): 

help print 

help find 

# 3.2 Lexical matters

The outer lexical syntax consists of three main categories of syntax tokens: 

1. major keywords the command names that are available in the present logic session; 

2. minor keywords additional literal tokens required by the syntax of commands; 

3. named tokens — various categories of identifiers etc. 

Major keywords and minor keywords are guaranteed to be disjoint. This helps user-interfaces to determine the overall structure of a theory text, without knowing the full details of command syntax. Internally, there is some additional information about the kind of major keywords, which approximates the command type (theory command, proof command etc.). 

Keywords override named tokens. For example, the presence of a command called term inhibits the identifier term, but the string "term" can be used instead. By convention, the outer syntax always allows quoted strings in addition to identifiers, wherever a named entity is expected. 

When tokenizing a given input sequence, the lexer repeatedly takes the longest prefix of the input that forms a valid token. Spaces, tabs, newlines and formfeeds between tokens serve as explicit separators. 

The categories for named tokens are defined once and for all as follows. 

```txt
short IDENT = letter (substring? quasiletter)*  
long IDENT = short IDENT(.short IDENT)  
sym IDENT = sym + | \\<short IDENT>  
nat = digit+  
float = nat.nat | -nat.nat  
term_var = ?short IDENT | ?short IDENT.nat  
type IDENT = 'short IDENT  
type_var = ?type IDENT | ?type IDENT.nat  
string = '' ... ''  
altstring = ' ... '  
cartouche = \\<open> ... \\<close>  
verbatimim = {* ... *}  
letter = latin | \\<latin> | \\<latin latin> | greek |  
subscript = \\<^sub>  
quasiletter = letter | digit | _ | '  
latin = a | ... | z | A | ... | Z  
digit = 0 | ... | 9  
sym = ! | # | $ | % | & | * | + | - | / | < | = > | ? | @ | ^ | _ | | ~  
greek = \\<alpha> | \\<beta> | \\<gamma> | \\<delta> | \\<epsilon> | \\<zeta> | \\<eta> | \\<theta> | \\<iota> | \\<kappa> | \\<mu> | \\<nu> | \\<xi> | \\<rho> | \\<sigma> | \\<tau> | \\<upsilon> | \\<phi> | \\<chi> | \\<psi> | \\<omega> | \\<Delta> | \\<Theta> | \\<Lambda> | \\<Xi> | \\<Pi> | \\<Psi> | \\<Omega> 
```

A term_var or type_var describes an unknown, which is internally a pair of base name and index (ML type indexname). These components are either separated by a dot as in $\ell x . 1$ or $\ell x 7 . 3$ or run together as in $? x 1$ . The latter form is possible if the base name does not end with digits. If the index is 0, it may be dropped altogether: $\ell x$ and $\ell x 0$ and $\it { ? } x . 0$ all refer to the same unknown, with basename $x$ and index 0. 

The syntax of string admits any characters, including newlines; “"” (doublequote) and “\” (backslash) need to be escaped by a backslash; arbitrary character codes may be specified as $" \textmd { d } d d ^ { \prime \prime }$ , with three decimal digits. Alternative strings according to altstring are analogous, using single back-quotes instead. 

The body of verbatim may consist of any text not containing “*}”; this allows 

to include quotes without further escapes, but there is no way to escape “*}”. Cartouches do not have this limitation. 

A cartouche consists of arbitrary text, with properly balanced blocks of “\<open> . . . \<close>”. Note that the rendering of cartouche delimiters is usually like this: “‹ . . . ›”. 

Source comments take the form (* . . . *) and may be nested: the text i s removed after lexical analysis of the input and thus not suitable for documentation. The Isar syntax also provides proper document comments that are considered as part of the text (see §3.3.5). 

Common mathematical symbols such as $\forall$ are represented in Isabelle as \<forall>. There are infinitely many Isabelle symbols like this, although proper presentation is left to front-end tools such as LATEX or Isabelle/jEdit. A list of predefined Isabelle symbols that work well with these tools is given in appendix B. Note that \<lambda> does not belong to the letter category, since it is already used differently in the Pure term language. 

# 3.3 Common syntax entities

We now introduce several basic syntactic entities, such as names, terms, and theorem specifications, which are factored out of the actual Isar language elements to be described later. 

# 3.3.1 Names

Entity name usually refers to any name of types, constants, theorems etc. Quoted strings provide an escape for non-identifier names or those ruled out by outer syntax keywords (e.g. quoted "let"). 

name 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/11c130196a5c0c431dd1b4fd67b33dff3c7918db778a925685879256cbf671f2.jpg)


par_name 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/282cc1821480ab0d2eba31a844338bf58af3e18ff018268f2aea707f6b41dfbf.jpg)


A system_name is like name, but it excludes white-space characters and needs to conform to file-name notation. Name components that are special on Windows (e.g. CON, PRN, AUX) are excluded on all platforms. 

# 3.3.2 Numbers

The outer lexical syntax (§3.2) admits natural numbers and floating point numbers. These are combined as int and real as follows. 

int 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9dbba794079e98d57f372ab519b1dd4cd06b4b9c879dd1f55947f183a074bf54.jpg)


real 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/02f4cee82fd4716cd40d45553692b7f69d43224d01e8459e77005c347dc3567d.jpg)


Note that there is an overlap with the category name, which also includes nat. 

# 3.3.3 Embedded content

Entity embedded refers to content of other languages: cartouches allow arbitrary nesting of sub-languages that respect the recursive balancing of cartouche delimiters. Quoted strings are possible as well, but require escaped quotes when nested. As a shortcut, tokens that appear as plain identifiers in the outer language may be used as inner language content without delimiters. 

embedded 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d942b82a1d7ed6e5aedc728d29f5f79e40652f76761e90fa5cd3a92d5194e54f.jpg)


# 3.3.4 Document text

A chunk of document text is usually given as cartouche ‹. . . ›. For convenience, any of the smaller text unit that conforms to name is admitted as well. 

text 

embedded 

Typical uses are document markup commands, like chapter, section etc. (§4.1). 

# 3.3.5 Document comments

Formal comments are an integral part of the document, but are logically void and removed from the resulting theory or term content. The output of document preparation (chapter 4) supports various styles, according to the following kinds of comments. 

• Marginal comment of the form \<comment> ‹text› or — ‹text›, usually with a single space between the comment symbol and the argument cartouche. The given argument is typeset as regular text, with formal antiquotations (§4.2). 

• Canceled text of the form \<^cancel>‹text› (no white space between the control symbol and the argument cartouche). The argument is typeset as formal Isabelle source and overlaid with a “strike-through” pattern, e.g. ////bad. 

• Raw LATEX source of the form \<^latex>‹argument› (no white space between the control symbol and the argument cartouche). This allows to augment the generated TEX source arbitrarily, without any sanity checks! 

These formal comments work uniformly in outer syntax, inner syntax (term language), Isabelle/ML, and some other embedded languages of Isabelle. 

# 3.3.6 Type classes, sorts and arities

Classes are specified by plain names. Sorts have a very simple inner syntax, which is either a single class name $c$ or a list $\{ c _ { 1 } , . . . , c _ { n } \}$ referring to the intersection of these classes. The syntax of type arities is given directly at the outer level. 

# classdecl

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/23cf88779e3b1ecf34f2e05b839b72b3ede257c2b4db0a66725760118eb696d0.jpg)


arity 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b83e4019e5322f68f4bf682cf68a4b0ae0a875f42aa90a6eb36bbabfbf250a36.jpg)


# 3.3.7 Types and terms

The actual inner Isabelle syntax, that of types and terms of the logic, is far too sophisticated in order to be modelled explicitly at the outer theory level. Basically, any such entity has to be quoted to turn it into a single token (the parsing and type-checking is performed internally later). For convenience, a slightly more liberal convention is adopted: quotes may be omitted for any type or term that is already atomic at the outer level. For example, one may just write x instead of quoted "x". Note that symbolic identifiers (e.g. $^ { + + }$ or $\forall$ are available as well, provided these have not been superseded by commands or other keywords already (such as = or $^ +$ ). 

type 

embedded 

term 

embedded 

prop 

embedded 

Positional instantiations are specified as a sequence of terms, or the placeholder “_” (underscore), which means to skip a position. 

inst 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/edd5cb2a20c0acdbb81169489bd38d8b3d2331063c10132115449f72cce0951e.jpg)


insts 

inst 

Named instantiations are specified as pairs of assignments $v = t$ , which refer to schematic variables in some theorem that is instantiated. Both type and terms instantiations are admitted, and distinguished by the usual syntax of variable names. 

named_inst 

variable 

type 

term 

named_insts 

named_inst 

and 

variable 

name 

term_var 

type_ident 

type_var 

Type declarations and definitions usually refer to typespec on the left-hand side. This models basic type constructor application at the outer syntax level. Note that only plain postfix notation is available here, but no infixes. 

typeargs 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/37a6dcd5197b31f2e02604f57224462787041ebc31bf2d165f8bf9e927bb2935.jpg)


typeargs_sorts 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0ae92fa20e480be2f89a103ef360d33527e0849fece1b9b1a6136b02242b0b85.jpg)


typespec 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/23f58537a7c1b0cc1e61de0f3a55de74e56b809a211e83f50962a34ea61d9aa8.jpg)


typespec_sorts 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/3698618e0d87febf55b2aaecb3ffb76c4c3ab7418dd13ca96e9bc6bb08b5c81e.jpg)


# 3.3.8 Term patterns and declarations

Wherever explicit propositions (or term fragments) occur in a proof text, casual binding of schematic term variables may be given specified via patterns of the form “(is $p _ { 1 } \ldots p _ { n }$ )”. This works both for term and prop. 

term_pat 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/70791da508a99514f973e837f47be60313583ee68bb83f81c7b71a019ccfb7d7.jpg)


prop_pat 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d1e8a86adcbd31b8eb9989dced47a9e2becd9466fad54b8036c7115dbf8035c8.jpg)


Declarations of local variables $x : : \tau$ and logical propositions $a : \varphi$ represent different views on the same principle of introducing a local scope. In practice, one may usually omit the typing of vars (due to type-inference), and the naming of propositions (due to implicit references of current facts). In any case, Isar proof elements usually admit to introduce multiple such items simultaneously. 

vars 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9e668cf75bff29d974abd69df97cceb968c96aa111427048155eacb21ee1ca19.jpg)


props 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fb636085a9eda943fa0643b850e3bab1f9872351517af1b867ee3f7fa7c701eb.jpg)


props 0 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/f4909ca0df8f07f52bc39daa58ae3f1e9981b3da2d88ee47899677e94601e31c.jpg)


The treatment of multiple declarations corresponds to the complementary focus of vars versus props. In “ $x _ { 1 }$ . . . $x _ { n } : : \tau$ ” the typing refers to all variables, while in a: ϕ1 . . . ϕn the naming refers to all propositions collectively. Isar language elements that refer to vars or props typically admit separate typings or namings via another level of iteration, with explicit and separators; e.g. see fix and assume in $\ S 6 . 2 . 1$ . 

# 3.3.9 Attributes and theorems

Attributes have their own “semi-inner” syntax, in the sense that input conforming to args below is parsed by the attribute a second time. The attribute argument specifications may be any sequence of atomic entities (identifiers, strings etc.), or properly bracketed argument lists. Below atom refers to any atomic entity, including any keyword conforming to sym_ident. 

atom 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/f7aeeb12590248f70cf520309ebca5fb00e2d815243328789d32a5ad60d288f7.jpg)


arg 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/12dfb0a60f954171bdab3b8b41390578ca59fac079e38887e9f185b026217549.jpg)


args 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/72334ea9d727696393e010a6428b8878af897cf04d05afe86fcd77173cc27e4a.jpg)


attributes 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fe996e737df33685912f2c3110b18d865e1d052c5fd29bcc3dd5a835a0e4a5a9.jpg)


Theorem specifications come in several flavors: axmdecl and thmdecl usually refer to axioms, assumptions or results of goal statements, while thmdef collects lists of existing theorems. Existing theorems are given by thm and thms, the former requires an actual singleton result. 

There are three forms of theorem references: 

1. named facts $a$ , 

2. selections from named facts $a ( i )$ or $a ( j \mathrm { ~ - ~ } k )$ 

3. literal fact propositions using token syntax altstring $^ { c } \varphi ^ { \mathfrak { c } }$ or cartouche $\left. \varphi \right.$ (see also method fact). 

Any kind of theorem specification may include lists of attributes both on the left and right hand sides; attributes are applied to any immediately preceding fact. If names are omitted, the theorems are not stored within the theorem database of the theory or proof context, but any given attributes are applied nonetheless. 

An extra pair of brackets around attributes (like “ $[ [ s i m p r o c ~ a ] ] " )$ abbreviates a theorem reference involving an internal dummy fact, which will be ignored 

later on. So only the effect of the attribute on the background context will persist. This form of in-place declarations is particularly useful with commands like declare and using. 

axmdecl 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/954cbd975f509955a5bf57656e39b995f0625ffea02bef1f73d560510008ebfc.jpg)


thmbind 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/6d60847b92e1a7b312c2a3227b4ccc03e77727a92d10cc5b9365edbfa38dcd8a.jpg)


thmdecl 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2b2732ce66b71791fc340651a156f52b2fed0c6afa8e1077ac00b9b60434bc1d.jpg)


thmdef 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5806600dbbf48a2df8b60b75af98289872a4943ac399cb7f410a3b49aef4b847.jpg)


thm 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a9e5a059c72804067e96de10d62be2cfd86433f15e4681708306f990bd7b1787.jpg)


thms 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/092033966e9295f77522515e41401f4a7785c9630e0ef8aa3f6616ff3e2368c9.jpg)


selection 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4d157f46248eaa97507a60df019ed4a8dabda417ae1b20b54f20e2e6b84cb88f.jpg)


# 3.3.10 Structured specifications

Structured specifications use propositions with explicit notation for the “eigen-context” to describe rule structure: $\Lambda x$ . A $x \implies . . . \implies B \ x$ is expressed as $\textit { B x }$ $x$ if $A$ $x$ and . . . for $x$ . It is also possible to use dummy terms “_” (underscore) to refer to locally fixed variables anonymously. 

Multiple specifications are delimited by “|” to emphasize separate cases: each with its own scope of inferred types for free variables. 

for_fixes 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e4cda9e67c4947c96b19e8078aaa2ca83176da043c034d1d3e61bfffdd2b784c.jpg)


multi_specs 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/10955f14c2747d9b63fb9611c39d154e7a24eb3b09dec90f763888a9b8194d21.jpg)


structured_spec 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/cfc102691aa29f4bcd634b61961d4231b2d2aac03e68116908019d246231c503.jpg)


spec_prems 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/efdef7488c5aa02b4a884b20341b44a22eec355ff509cb834285c622f424f816.jpg)


specification 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9de48521f2591d0663231da17792ce235e3200b18a86fc78481940626aecc97a.jpg)


# 3.4 Diagnostic commands

print_theory\*: context $\rightarrow$ print Definitions\*: context $\rightarrow$ print_methods\*: context $\rightarrow$ print_attribute\*: context $\rightarrow$ print_theorems\*: context $\rightarrow$ find_theorems\*: context $\rightarrow$ find_consts\*: context $\rightarrow$ thm_deps\*: context $\rightarrow$ unused_thms\*: context $\rightarrow$ print_facts\*: context $\rightarrow$ print_term bindings\*: context $\rightarrow$ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5e65ce7fa45a383ed8daddebaa40e626d62662d8123f47316cf4d9bd849e37a8.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/8df17fed41c800fdc3138655a6faf845ca832925d0af8317fd4ef9ad92d87dac.jpg)


thm_criterion 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/861387ea70ec07e7fce0123f0d2b830f66f829381560eeb04e97a2ff94801b0a.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/902d3a883fab0d6253ea12c56561475f2a9725c4e8705341e10ecdcd9734373f.jpg)


const_criterion 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2c28361a47a9dd6ef192f3031d091a7e28b1b6b44f542db1070d350e09a759eb.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/cb10037b81cef37b291500d959b81fe441f307b001e95bc0094253e4fc4a689b.jpg)


These commands print certain parts of the theory and proof context. Note that there are some further ones available, such as for the set of rules declared for simplifications. 

print_theory prints the main logical content of the background theory; the “!” option indicates extra verbosity. 

print_definitions prints dependencies of definitional specifications within the background theory, which may be constants (§5.4, §5.9) or types (§5.12.2, §11.7); the “!” option indicates extra verbosity. 

print_methods prints all proof methods available in the current theory context; the “!” option indicates extra verbosity. 

print_attributes prints all attributes available in the current theory context; the “!” option indicates extra verbosity. 

print_theorems prints theorems of the background theory resulting from the last command; the “!” option indicates extra verbosity. 

print_facts prints all local facts of the current context, both named and unnamed ones; the “!” option indicates extra verbosity. 

print_term_bindings prints all term bindings that are present in the context. 

find_theorems criteria retrieves facts from the theory or proof context matching all of given search criteria. The criterion name: $p$ selects all theorems whose fully qualified name matches pattern $p$ , which may contain “ $^ *$ ” wildcards. The criteria intro, elim, and dest select theorems that match the current goal as introduction, elimination or destruction rules, respectively. The criterion solves returns all rules that would directly solve the current goal. The criterion simp: $t$ selects all rewrite 

rules whose left-hand side matches the given term. The criterion term $t$ selects all theorems that contain the pattern $t$ – as usual, patterns may contain occurrences of the dummy “_”, schematic variables, and type constraints. 

Criteria can be preceded by “ $-$ ” to select theorems that do not match. Note that giving the empty list of criteria yields all currently known facts. An optional limit for the number of printed facts may be given; the default is 40. By default, duplicates are removed from the search result. Use with_dups to display duplicates. 

find_consts criteria prints all constants whose type meets all of the given criteria. The criterion strict: ty is met by any type that matches the type pattern ty. Patterns may contain both the dummy type “_” and sort constraints. The criterion ty is similar, but it also matches against subtypes. The criterion name: $p$ and the prefix “ $-$ ” function as described for find_theorems. 

thm_deps thms prints immediate theorem dependencies, i.e. the union of all theorems that are used directly to prove the argument facts, without going deeper into the dependency graph. 

unused_thms $A _ { 1 }$ . . . Am − B1 . . . $B _ { n }$ displays all theorems that are proved in theories $B _ { 1 }$ . . . $B _ { n }$ or their parents but not in $A _ { 1 }$ . . . $A _ { m }$ or their parents and that are never used. If $\boldsymbol { n }$ is $0$ , the end of the range of theories defaults to the current theory. If no range is specified, only the unused theorems in the current theory are displayed. 

# Document preparation

Isabelle/Isar provides a simple document preparation system based on PDF-LATEX, with support for hyperlinks and bookmarks within that format. This allows to produce papers, books, theses etc. from Isabelle theory sources. 

LATEX output is generated while processing a session in batch mode, as explained in the The Isabelle System Manual [54]. The main Isabelle tools to get started with document preparation are isabelle mkroot and isabelle build. 

The classic Isabelle/HOL tutorial [38] also explains some aspects of theory presentation. 

# 4.1 Markup commands

chapter : any → any 

section : $a n y  a n y$ 

subsection : $a n y  a n y$ 

subsubsection : $a n y  a n y$ 

paragraph : $a n y  a n y$ 

subparagraph : $a n y  a n y$ 

text : $a n y  a n y$ 

txt : $a n y  a n y$ 

text_raw : $a n y  a n y$ 

Markup commands provide a structured way to insert text into the document generated from a theory. Each markup command takes a single text argument, which is passed as argument to a corresponding LATEX macro. The default macros provided by ~~/lib/texinputs/isabelle.sty can be redefined according to the needs of the underlying document and LATEX styles. 

Note that formal comments (§3.3.5) are similar to markup commands, but have a different status within Isabelle/Isar syntax. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fa2bc0a804036cb69759a635f4623c977bbdc3597ddabfcc4015632e68b6a7c8.jpg)


chapter, section, subsection etc. mark section headings within the theory source. This works in any context, even before the initial theory command. The corresponding LATEX macros are \isamarkupchapter, \isamarkupsection, \isamarkupsubsection etc. 

text and txt specify paragraphs of plain text. This corresponds to a LATEX environment \begin{isamarkuptext} . . . \end{isamarkuptext} etc. 

text_raw is similar to text, but without any surrounding markup environment. This allows to inject arbitrary LATEX source into the generated document. 

All text passed to any of the above markup commands may refer to formal entities via document antiquotations, see also §4.2. These are interpreted in the present theory or proof context. 

The proof markup commands closely resemble those for theory specifications, but have a different formal status and produce different LATEX macros. 

# 4.2 Document antiquotations

theory : antiquotation 

thm : antiquotation 

lemma : antiquotation 

prop : antiquotation 

term : antiquotation 

term_type : antiquotation 

typeof : antiquotation 

const : antiquotation 

abbrev : antiquotation 

typ : antiquotation 

type : antiquotation 

class : antiquotation 

locale : antiquotation 

bundle : antiquotation 

text : antiquotation 

goals : antiquotation 

subgoals : antiquotation 

prf : antiquotation 

full_prf : antiquotation 

ML_text : antiquotation 

ML : antiquotation 

ML_def : antiquotation 

ML_ref : antiquotation 

ML_infix : antiquotation 

ML_infix_def : antiquotation 

ML_infix_ref : antiquotation 

ML_type : antiquotation 

ML_type_def : antiquotation 

ML_type_ref : antiquotation 

ML_structure : antiquotation 

ML_structure_def : antiquotation 

ML_structure_ref : antiquotation 

ML_functor : antiquotation 

ML_functor_def : antiquotation 

ML_functor_ref : antiquotation 

emph : antiquotation  
bold : antiquotation  
verbatim : antiquotation  
bash_function : antiquotation  
system_option : antiquotation  
session : antiquotation  
file : antiquotation  
url : antiquotation  
cite : antiquotation  
nocite : antiquotation  
citet : antiquotation  
citep : antiquotation  
print_antiquotations* : context → 

The overall content of an Isabelle/Isar theory may alternate between formal and informal text. The main body consists of formal specification and proof commands, interspersed with markup commands (§4.1) or document comments (§3.3.5). The argument of markup commands quotes informal text to be printed in the resulting document, but may again refer to formal entities via document antiquotations. 

For example, embedding @{term [show_types] "f $\textbf { x } = \textbf { a } + \textbf { x } ^ { \prime \prime } \}$ within a text block makes ( $f { \mathrel { : } } { \mathrel { : } } ^ { \prime } a \Rightarrow { \mathrm { ~ } } ^ { \prime } a )$ $( x ! : ^ { \prime } a ) = ( a ! : ^ { \prime } a ) + x$ appear in the final LATEX document. 

Antiquotations usually spare the author tedious typing of logical entities in full detail. Even more importantly, some degree of consistency-checking between the main body of formal text and its informal explanation is achieved, since terms and types appearing in antiquotations are checked within the current theory or proof context. 

Antiquotations are in general written as @{name [options] arguments}. The short form \<^name>‹argument_content› (without surrounding $\mathbb { Q } \{ . . . \}$ ) works for a single argument that is a cartouche. A cartouche without special decoration is equivalent to \<^cartouche>‹argument_content›, which is equivalent to @{cartouche ‹argument_content›}. The special name cartouche is defined in the context: Isabelle/Pure introduces that as an alias to text (see below). Consequently, $\langle f o o \_ b a r \ + \ b a z \\\le \ b a z a r \rangle$ prints literal quasi-formal text (unchecked). A control symbol \<^name> within the body text, but without a subsequent cartouche, is equivalent to $\Theta \{ n a m e \}$ . 

antiquotation 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b89978bc8803df4f5a2f79313355f4ce71c5e387dc3ce9e49505b27810eb212a.jpg)


options 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/713d1c9c00ffcf164e33864eae2d068a14ab772fb1cc34b2db6f115eba8770f2.jpg)


option 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/567f7701be53f30d16a6a03c51fb456f6d1042ceeee3eb90ffbb45544d471730.jpg)


Note that the syntax of antiquotations may not include source comments $( * \dots * )$ nor verbatim text $\{ * \ldots * \}$ . 

antiquotation_body 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/56bdf254b9a4236e850929306a4427b4946d2d2cd7dff3f59d1cfb1dc9f7533a.jpg)


# antiquotation

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ab4496454fab7f5f0fe3d1a09dfc3fdb3fd2e5192f0fe35aa6129712a09eba1d.jpg)


styles 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/dd2b7411ec51232c38e07aa3cd41a809060ac645bdae49dab30945771d973e66.jpg)


style 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/30f1748b450c743e74ac9e71cc218c3e3403695b90fe31082667dfcf514b1ce9.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/512aec68d426979dd5835d20458866857b84bdcf2cebdc1ba8fee3d53e52edc1.jpg)


$@ \{ t e x t s \}$ prints uninterpreted source text $s$ , i.e. inner syntax. This is particularly useful to print portions of text according to the Isabelle document style, without demanding well-formedness, e.g. small pieces of terms that should not be parsed or type-checked yet. 

It is also possible to write this in the short form ‹s› without any further decoration. 

${ \textcircled { \mathrm { 2 } } } \{ { t h e o r y \_ t e x t \ s } \}$ prints uninterpreted theory source text $s$ , i.e. outer syntax with command keywords and other tokens. 

$\mathbb { Q } \{ t h e o r y . t \}$ prints the session-qualified theory name $A$ , which is guaranteed to refer to a valid ancestor theory in the current context. 

$ @ \{ { t h m ~ a _ { 1 } } _ { \cdot \cdot \cdot } { } _ { } \{ { a _ { n } } \}$ prints theorems $a _ { 1 }$ . . . $a _ { n }$ . Full fact expressions are allowed here, including attributes (§3.3.9). 

${ \mathfrak { Q } } \{ p r o p \ \varphi \}$ prints a well-typed proposition $\varphi$ 

$ @ \{ l e m m a \ \varphi \ b y \ m \}$ proves a well-typed proposition $\varphi$ by method $m$ and prints the original $\varphi$ . 

$@ \{ t e r m \ t \}$ prints a well-typed term $t$ . 

$@ \{ v a l u e \ t \}$ evaluates a term $t$ and prints its result, see also value. 

${ \mathbb { O } } \{ t e r m \_ t y p e \ t \}$ prints a well-typed term $t$ annotated with its type. 

$@ \{ t y p e o f t \}$ prints the type of a well-typed term $t$ 

$@ \{ c o n s t \ c \}$ prints a logical or syntactic constant $c$ 

$ @ \{ a b b r e v \ c \ x _ { 1 } \ . . . \ x _ { n } \}$ prints a constant abbreviation c x1 . . . $x _ { n } \equiv r h s$ as defined in the current context. 

$@ \{ t y p \ \tau \}$ prints a well-formed type $\tau$ . 

$@ \{ t y p e \ \kappa \}$ prints a (logical or syntactic) type constructor $\kappa$ 

$@ \{ c l a s s ~ c \}$ prints a class c. 

$@ \{ l o c a l e \ c \}$ prints a locale c. 

$@ \{ b u n d l e \ c \}$ prints a bundle c. 

${ \ @ \{ c o m m a n d ~ n a m e \} }$ , $@ \{ m e t h o d ~ n a m e \}$ , $ @ \{ a t t r i b u t e ~ n a m e \}$ print checked entities of the Isar language. 

$@ \{ g o a l s \}$ prints the current dynamic goal state. This is mainly for support of tactic-emulation scripts within Isar. Presentation of goal states does not conform to the idea of human-readable proof documents! 

When explaining proofs in detail it is usually better to spell out the reasoning via proper Isar proof commands, instead of peeking at the internal machine configuration. 

$@ \{ s u b g o a l s \}$ is similar to $@ \{ g o a l s \}$ , but does not print the main goal. 

$@ \{ p r f \ a _ { 1 } \ \dots \ a _ { n } \}$ prints the (compact) proof terms corresponding to the theorems $a _ { 1 }$ . . . $a _ { n }$ . Note that this requires proof terms to be switched on for the current logic session. 

$ @ \{ f u l l \_ p r f \ a _ { 1 } \ \dots \ a _ { n } \}$ is like $@ \{ p r f \ a _ { 1 } \ \dots \ a _ { n } \}$ , but prints the full proof terms, i.e. also displays information omitted in the compact proof term, which is denoted by “_” placeholders there. 

${ \mathbb { O } } \{ M L \_ t e x t s \}$ prints ML text verbatim: only the token language is checked. 

$@ \{ M L \ s \}$ , ${ \mathbb { O } } \{ M L \_ i n \hbar x \ s \}$ , $ @ \{ M L \_ t y p e \ s \}$ , ${ \ @ \{ M L \_ s t r u c t u r e s \} }$ , and $ @ \{ M L \_ f u n c t o r \ s \}$ check text $s$ as ML value, infix operator, type, exception, structure, and functor respectively. The source is printed verbatim. The variants ${ \mathbb O } \{ M L \_ d e f \ s \}$ and ${ \ @ \{ M L \_ r e f \ s \} }$ etc. maintain the document index: “def” means to make a bold entry, “ref” means to make a regular entry. 

There are two forms for type constructors, with or without separate type arguments: this impacts only the index entry. For example, ${ \ @ \{ M L \_ t y p e \_ r e f \ \ast ^ { \prime } a \ l i s t \rangle } \}$ makes an entry literally for “ 0a list” (sorted under the letter “a”), but ${ \ @ \{ M L \_ t y p e \_ r e f \prime a \ \cdot l i s t \} }$ makes an entry for the constructor name “list”. 

$@ \{ e m p h \ s \}$ prints document source recursively, with LATEX markup $\backslash \mathrm { e m p h } \{ \dots \}$ . 

$@ \{ b o l d \textit { \textbf { s } } \}$ prints document source recursively, with LATEX markup \textbf{. . . }. 

$@ \{ v e r b a t i m s \}$ prints uninterpreted source text literally as ASCII characters, using some type-writer font style. 

${ \ @ \{ b a s h \_ f u n c t i o n \ n a m e \} }$ prints the given GNU bash function verbatim. The name is checked wrt. the Isabelle system environment [54]. 

${ \mathbb O } \{ s y s t e m \_ o p t i o n \ n a m e \}$ prints the given system option verbatim. The name is checked wrt. cumulative etc/options of all Isabelle components, notably ~~/etc/options. 

$@ \{ s e s s i o n \ n a m e \}$ prints given session name verbatim. The name is checked wrt. the dependencies of the current session. 

$@ \{ p a t h \ n a m e \}$ prints the file-system path name verbatim. 

$@ \{ f l l e \ n a m e \}$ is like $@ \{ p a t h \ n a m e \}$ , but ensures that name refers to a plain file. 

$@ \{ d i r \ n a m e \}$ is like $@ \{ p a t h \ n a m e \}$ , but ensures that name refers to a directory. 

$@ \{ u r l n a m e \}$ produces markup for the given URL, which results in an active hyperlink within the text. 

$@ \{ c i t e \ a r g \}$ produces the BibTEX citation macro \cite[...]{...} with its optional and mandatory argument. The analogous \nocite, and the \citet and \citep variants from the natbib package1 are supported as well. 

The argument syntax is uniform for all variants and is usually presented in control-symbol-cartouche form: cite ‹arg›. The formal syntax of the nested argument language is defined as follows: 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e7df379fcaa8a294b9ef838912ac89dc878e4ce2d66872fa3af49b8d14140e47.jpg)


Here the embedded text is free-form LATEX, which becomes the optional argument of the \cite macro. The named items are BibTEX database entries and become the mandatory argument (separated by comma). The optional part “using name” specifies an alternative LATEX macro name. 

print_antiquotations prints all document antiquotations that are defined in the current context; the “!” option indicates extra verbosity. 

# 4.2.1 Styled antiquotations

The antiquotations thm, prop and term admit an extra style specification to modify the printed result. A style is specified by a name with a possibly empty number of arguments; multiple styles can be sequenced with commas. The following standard styles are available: 

lhs extracts the first argument of any application form with at least two arguments — typically meta-level or object-level equality, or any other binary relation. 

rhs is like lhs, but extracts the second argument. 

concl extracts the conclusion $C$ from a rule in Horn-clause normal form $A _ { 1 }$ =⇒ . . . $A _ { n } \Longrightarrow C$ . 

prem n extract premise number $\boldsymbol { n }$ from from a rule in Horn-clause normal form A =⇒ . . . $A _ { n } \Longrightarrow C$ . 

# 4.2.2 General options

The following options are available to tune the printed output of antiquotations. Note that many of these coincide with system and configuration options of the same names. 

show_types = bool and show_sorts = bool control printing of explicit type and sort constraints. 

show_structs = bool controls printing of implicit structures. 

show_abbrevs = bool controls folding of abbreviations. 

names_long = bool forces names of types and constants etc. to be printed in their fully qualified internal form. 

names_short = bool forces names of types and constants etc. to be printed unqualified. Note that internalizing the output again in the current context may well yield a different result. 

names_unique = bool determines whether the printed version of qualified names should be made sufficiently long to avoid overlap with names declared further back. Set to false for more concise output. 

eta_contract = bool prints terms in $\eta$ -contracted form. 

$d i s p l a y = b o o l$ indicates if the text is to be output as multi-line “display material”, rather than a small piece of text without line breaks (which is the default). 

In this mode the embedded entities are printed in the same style as the main theory text. 

$b r e a k = b o o l$ controls line breaks in non-display material. 

cartouche = bool indicates if the output should be delimited as cartouche. 

$q u o t e s = b o o l$ indicates if the output should be delimited via double quotes (option cartouche takes precedence). Note that the Isabelle LATEX styles may suppress quotes on their own account. 

$m o d e = n a m e$ adds name to the print mode to be used for presentation. Note that the standard setup for LATEX output is already present by default, with mode “latex”. 

margin = nat and $i n d e n t = n a t$ change the margin or indentation for pretty printing of display material. 

goals_limit = nat determines the maximum number of subgoals to be printed (for goal-based antiquotation). 

$s o u r c e = b o o l$ prints the original source text of the antiquotation arguments, rather than its internal representation. Note that formal checking of thm, term, etc. is still enabled; use the text antiquotation for unchecked output. 

Regular term and typ antiquotations with $s o u r c e = f a l s e$ involve a full round-trip from the original source to an internalized logical entity back to a source form, according to the syntax of the current context. Thus the printed output is not under direct control of the author, it may even fluctuate a bit as the underlying theory is changed later on. 

In contrast, $s o u r c e = t r u e$ admits direct printing of the given source text, with the desirable well-formedness check in the background, but without modification of the printed text. 

Cartouche delimiters of the argument are stripped for antiquotations that are internally categorized as “embedded”. 

source_cartouche is like source, but cartouche delimiters are always preserved in the output. 

For Boolean flags, “ $n a m e = t r u e ^ { , \gamma }$ may be abbreviated as “name”. All of the above flags are disabled by default, unless changed specifically for a logic session in the corresponding ROOT file. 

# 4.3 Markdown-like text structure

The markup commands text, txt, text_raw (§4.1) consist of plain text. Its internal structure consists of paragraphs and (nested) lists, using special Isabelle symbols and some rules for indentation and blank lines. This quasivisual format resembles Markdown2, but the full complexity of that notation is avoided. 

This is a summary of the main principles of minimal Markdown in Isabelle: 

• List items start with the following markers 

```txt
itemize: \<^item>   
列出： \<^enum>   
描述： \<^descr>
```

• Adjacent list items with same indentation and same marker are grouped into a single list. 

• Singleton blank lines separate paragraphs. 

• Multiple blank lines escape from the current list hierarchy. 

Notable differences to official Markdown: 

• Indentation of list items needs to match exactly. 

• Indentation is unlimited (official Markdown interprets four spaces as block quote). 

• List items always consist of paragraphs — there is no notion of “tight” list. 

• Section headings are expressed via Isar document markup commands (§4.1). 

• URLs, font styles, other special content is expressed via antiquotations (§4.2), usually with proper nesting of sub-languages via text cartouches. 

# 4.4 Document markers and command tags

Document markers are formal comments of the form $\circledast$ ‹marker_body› (using the control symbol \<^marker>) and may occur anywhere within the outer syntax of a command: the inner syntax of a marker body resembles that for attributes (§3.3.9). In contrast, Command tags may only occur after a command keyword and are treated as special markers as explained below. 

marker 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d91eed191e0ef03590adfa72057ac055ee6665730ea3ce2ac65bf25b4e054c66.jpg)


marker_body 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9176b4a3c7ccd01fdc0e015b3e8f1026add5063fc7773a38d3e439dd4557145d.jpg)


tags 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b229c5e733404448900ab1cc3b9f64f64839d99f24accfc18a1f8f96f38bd5ed.jpg)


tag 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ae13850b115584ac0b55383f38fb2f2d1a3214faafed5dba568ae10663ccbaa4.jpg)


Document markers are stripped from the document output, but surrounding white-space is preserved: e.g. a marker at the end of a line does not affect the subsequent line break. Markers operate within the semantic presentation context of a command, and may modify it to change the overall appearance of a command span (e.g. by adding tags). 

Each document marker has its own syntax defined in the theory context; the following markers are predefined in Isabelle/Pure: 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4b6eef0640a41d3225c0cfc68bd554660313a5202e08b603633f640df42c4e3d.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b0bca7ca6ebe24aacbf13dfe03b34c1c82d939b76c724b2ac0e49e162b25f14f.jpg)


scope 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7f73a7510ff786f36bdc7a96e0ee2acacdd6634ae9071493963d11cd00990a49.jpg)


✐‹title arg›, $\circledast$ ‹creator arg›, $\mathcal { P }$ ‹contributor arg›, $\mathcal { P }$ ‹date arg›, $\scriptstyle { \mathcal { P } }$ ‹license arg›, and $\mathcal { P }$ ‹description arg› produce markup in the PIDE document, without any immediate effect on typesetting. This vocabulary is taken from the Dublin Core Metadata Initiative3. The argument is an uninterpreted string, except for description, which consists of words that are subject to spell-checking. 

✐‹tag name› updates the list of command tags in the presentation context: later declarations take precedence, so ✐‹tag a, tag b, tag c› produces a reversed list. The default tags are given by the original keywords declaration of a command, and the system option document_tags. 

The optional scope tells how far the tagging is applied to subsequent proof structure: “(proof )” means it applies to the following proof text, and “(command)” means it only applies to the current command. The default within a proof body is “(proof )”, but for toplevel goal statements it is “(command)”. Thus a tag marker for theorem, lemma etc. does not affect its proof by default. 

An old-style command tag %name is treated like a document marker ✐‹tag (proof ) name›: the list of command tags precedes the list of document markers. The head of the resulting tags in the presentation context is turned into LATEX environments to modify the type-setting. The following tags are pre-declared for certain classes of commands, and serve as default markup for certain kinds of commands: 

document document markup commands 

theory theory begin/end 

proof all proof commands 

ML all commands involving ML code 

The Isabelle document preparation system [54] allows tagged command regions to be presented specifically, e.g. to fold proof texts, or drop parts of the text completely. 

For example “by auto ✐‹tag invisible›” causes that piece of proof to be treated as invisible instead of proof (the default), which may be shown or hidden depending on the document setup. In contrast, “by auto $\circledast$ ‹tag visible›” forces this text to be shown invariably. 

Explicit tag specifications within a proof apply to all subsequent commands of the same level of nesting. For example, “proof ✐‹tag invisible› . . . qed” forces the whole sub-proof to be typeset as visible (unless some of its parts are tagged differently). 

Command tags merely produce certain markup environments for typesetting. The meaning of these is determined by LATEX macros, as defined in ~~/lib/texinputs/isabelle.sty or by the document author. The Isabelle document preparation tools also provide some high-level options to specify the meaning of arbitrary tags to “keep”, “drop”, or “fold” the corresponding parts of the text. Logic sessions may also specify “document versions”, where given tags are interpreted in some particular way. Again see [54] for further details. 

# 4.5 Railroad diagrams

rail : antiquotation 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fc474be05a36cac891e9e440fcc7da8de9538fdaee6a962aa1988a8a8270f777.jpg)


The rail antiquotation allows to include syntax diagrams into Isabelle documents. LATEX requires the style file ~~/lib/texinputs/railsetup.sty, which can be used via \usepackage{railsetup} in root.tex, for example. The rail specification language is quoted here as Isabelle string or text cartouche; it has its own grammar given below. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1a4a3b8a3aa5d83f71d7d7eaf53cc45fb168ff069ec218d7ea16e666967bc632.jpg)


rule 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9cd6607a34e44e5e0d28dd1d93e2efd7c24760e143d3881b9018c4f6c42dc2e4.jpg)


body 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2eaa40a0d41003b8547318e846af7a5fbe5913c903154a4303aae3f0f7c68049.jpg)


concatenation 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b2310c44bd2641bf1ad657662d20e8bf017f429ca1688042fcbf42d5ab62abbb.jpg)


atom 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e0b139f42b4181dda73b37525e34c192607ef1caa6a41dfdd441f737cc73c4ca.jpg)


The lexical syntax of identifier coincides with that of short_ident in regular Isabelle syntax, but string uses single quotes instead of double quotes of the standard string category. 

Each rule defines a formal language (with optional name), using a notation that is similar to EBNF or regular expressions with recursion. The meaning and visual appearance of these rail language elements is illustrated by the following representative examples. 

• Empty () 

• Nonterminal A 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ae5790a23a52e2425b4ecebce9799f70442a4bf5d6a03305b79cbd16dc8b07bc.jpg)


• Nonterminal via Isabelle antiquotation @{syntax method} 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/79e28d93482e99734bcddd6d7135c3c09b631a6b1930576175751042668d0834.jpg)


• Terminal ’xyz’ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/02252487a6954564cd3d968b01d3774c634d417fea8740e2e68c56d62f1bbba2.jpg)


• Terminal in keyword style @’xyz’ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/86e60ab50ad847472f96842135fb6ac3862175a37462f9b30abf130d645ee838.jpg)


• Terminal via Isabelle antiquotation @@{method rule} 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2a6dfa92aa9834b557bda246086532996fe2e7a0b2e07f7321728dda7c57a068.jpg)


• Concatenation A B C 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/306d1c0d1d5456821fafc973dab3079b40babb5dc0cac3c4bfe50ba6711dbf8c.jpg)


• Newline inside concatenation A B C \<newline> D E F 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/3a3fcea913282619e8cd63d9a54456bb8567a343d5cd5b6411bf000b8c884d6a.jpg)


• Variants A | B | C 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c9f039cca1bcdd8da3423c08727b095a7604d421ad21c8bce35cd68b1b5fd70c.jpg)


• Option A ? 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fe2b9444ce993eb6af879d0ad2ecfd8ac7b1ad0f6695a89fcb0be325c259e4f5.jpg)


• Repetition A * 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/647bfdbb8fef2f7ca9d6927ad8d60f6c9beaa9bf5eb7e1f581011ba8a8886b42.jpg)


• Repetition with separator A * sep 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b90cebc19f37a5260cb35aabf016befbfa2e2052af2dd7bfa186e96c65bdcc85.jpg)


• Strict repetition A + 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e13e386a8046c1dc1a773ec01ed80e62a13f2bc3716fff37dffbd7a1a6e411e0.jpg)


• Strict repetition with separator A + sep 

✓A 

$s e p$ 

# Specifications

The Isabelle/Isar theory format integrates specifications and proofs, with support for interactive development by continuous document editing. There is a separate document preparation system (see chapter 4), for typesetting formal developments together with informal text. The resulting hyper-linked PDF documents can be used both for WWW presentation and printed copies. 

The Isar proof language (see chapter 6) is embedded into the theory language as a proper sub-language. Proof mode is entered by stating some theorem or lemma at the theory level, and left again with the final conclusion (e.g. via qed). 

# 5.1 Defining theories

theory : toplevel $\longrightarrow$ theory 

end : theory → toplevel 

thy_deps∗ : theory → 

Isabelle/Isar theories are defined via theory files, which consist of an outermost sequence of definition–statement–proof elements. Some definitions are self-sufficient (e.g. fun in Isabelle/HOL), with foundational proofs performed internally. Other definitions require an explicit proof as justification (e.g. function and termination in Isabelle/HOL). Plain statements like theorem or lemma are merely a special case of that, defining a theorem from a given proposition and its proof. 

The theory body may be sub-structured by means of local theory targets, such as locale and class. It is also possible to use context begin . . . end blocks to delimited a local theory context: a named context to augment a locale or class specification, or an unnamed context to refer to local parameters and assumptions that are discharged later. See §5.2 for more details. 

A theory is commenced by the theory command, which indicates imports of previous theories, according to an acyclic foundational order. Before the 

initial theory command, there may be optional document header material (like section or text, see §4.1). The document header is outside of the formal theory context, though. 

A theory is concluded by a final end command, one that does not belong to a local theory target. No further commands may follow such a global end. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/8e69c1ad0cc742b000f62cd772226e35d10a6961e128cff6d43361366c1e042c.jpg)


keywords 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/61f69c7cad6e998f000664229dfa3bc91727f6e39c678ca7298a59310fd15fd9.jpg)


keyword_decls 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/3e2a93bb6e18fb8653a025954d06661ba542332763c733e242f0f58c8373bfc7.jpg)


abbrevs 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d5d652165a7b50cfe92f54e8ec5e6a43412e00e67a10e9a27b9a29e948dd9bc7.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/44a3949161b4ec80c0790691b848e49c0eddcc8db1a1b29ee4ce901a8b9ec266.jpg)


thy_bounds 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/6f6490d6f3a98579ddad08a14bd755317bee6ca1f1083d6605a3450157eabcc3.jpg)


theory $A$ imports $B _ { 1 }$ . . . $B _ { n }$ begin starts a new theory $A$ based on the merge of existing theories $B _ { 1 }$ . . . $B _ { n }$ . Due to the possibility to import more than one ancestor, the resulting theory structure of an Isabelle session forms a directed acyclic graph (DAG). Isabelle takes care that sources contributing to the development graph are always up-to-date: changed files are automatically rechecked whenever a theory header specification is processed. 

Empty imports are only allowed in the bootstrap process of the special theory Pure, which is the start of any other formal development based on Isabelle. Regular user theories usually refer to some more complex entry point, such as theory Main in Isabelle/HOL. 

The keywords specification declares outer syntax (chapter 3) that is introduced in this theory later on (rare in end-user applications). Both minor keywords and major keywords of the Isar command language need to be specified, in order to make parsing of proof documents work properly. Command keywords need to be classified according to their structural role in the formal text. Examples may be seen in Isabelle/HOL sources itself, such as keywords "typedef" :: thy_goal_defn or keywords "datatype" :: thy_defn for theory-level definitions with and without proof, respectively. Additional tags provide defaults for document preparation (§4.4). 

The abbrevs specification declares additional abbreviations for syntactic completion. The default for a new keyword is just its name, but completion may be avoided by defining abbrevs with empty text. 

end concludes the current theory definition. Note that some other commands, e.g. local theory targets locale or class may involve a begin that needs to be matched by end, according to the usual rules for nested blocks. 

thy_deps visualizes the theory hierarchy as a directed acyclic graph. By default, all imported theories are shown. This may be restricted by specifying bounds wrt. the theory inclusion relation. 

# 5.2 Local theory targets

context : theory → local_theory 

end : local_theory → theory 

private 

qualified 

A local theory target is a specification context that is managed separately within the enclosing theory. Contexts may introduce parameters (fixed variables) and assumptions (hypotheses). Definitions and theorems depending on the context may be added incrementally later on. 

Named contexts refer to locales (cf. §5.7) or type classes (cf. §5.8); the name “ $-$ ” signifies the global theory context. 

Unnamed contexts may introduce additional parameters and assumptions, and results produced in the context are generalized accordingly. Such auxiliary contexts may be nested within other targets, like locale, class, instantiation, overloading. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/82c87e26325f324badb94944f338169348bf49eb8bc6e0b52725972c301d465b.jpg)


target 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e10addf15b59bd8f6a17f66c712123785a7b71b76ec02fdb6cc9959b4c686aaa.jpg)


context c bundles begin opens a named context, by recommencing an existing locale or class $c$ . Note that locale and class definitions allow to include the begin keyword as well, in order to continue the local theory immediately after the initial specification. Optionally given bundles only take effect in the surface context within the begin / end block. 

context bundles elements begin opens an unnamed context, by extending the enclosing global or local theory target by the given declaration bundles (§5.3) and context elements (fixes, assumes etc.). This means any results stemming from definitions and proofs in the extended context will be exported into the enclosing target by lifting over extra parameters and premises. 

end concludes the current local theory, according to the nesting of contexts. Note that a global end has a different meaning: it concludes the theory itself (§5.1). 

private or qualified may be given as modifiers before any local theory command. This restricts name space accesses to the local scope, as determined by the enclosing context begin . . . end block. Outside its scope, a private name is inaccessible, and a qualified name is only accessible with some qualification. 

Neither a global theory nor a locale target provides a local scope by itself: an extra unnamed context is required to use private or qualified here. 

(in $c$ ) given after any local theory command specifies an immediate target, e.g. “definition (in c)” or “theorem (in c)”. This works both in a local or global theory context; the current target context will be suspended for this command only. Note that $\mathbf { \nabla } ^ { \langle } ( \mathbf { i n \mu } - \mathbf { \nabla } ) ^ { \mu }$ will always produce a global result independently of the current target context. 

Any specification element that operates on local_theory according to this manual implicitly allows the above target syntax (in $c$ ), but individual syntax diagrams omit that aspect for clarity. 

The exact meaning of results produced within a local theory context depends on the underlying target infrastructure (locale, type class etc.). The general idea is as follows, considering a context named $c$ with parameter $x$ and assumption $A [ x ]$ . 

Definitions are exported by introducing a global version with additional arguments; a syntactic abbreviation links the long form with the abstract version of the target context. For example, $a \equiv t [ x ]$ becomes c.a $\iota : \mathscr { x } \equiv t [ \mathscr { \ k { \mathscr { x } } } ]$ at the theory level (for arbitrary $\boldsymbol { \ell } \boldsymbol { x }$ ), together with a local abbreviation $a = c . a \ x$ in the target context (for the fixed parameter $x$ ). 

Theorems are exported by discharging the assumptions and generalizing the parameters of the context. For example, a: $B [ x ]$ becomes $c . a \colon A [ ? x ] \implies$ $B [ \ell x ]$ , again for arbitrary ? $\boldsymbol { \ell } \boldsymbol { x }$ . 

# 5.3 Bundled declarations

bundle : local_theory → local_theory 

bundle : theory → local_theory 

print_bundles∗ : context → 

include : $p r o o f ( s t a t e ) \to p r o o f ( s t a t e )$ 

including : $p r o o f ( p r o v e )  p r o o f ( p r o v e )$ 

includes : syntax 

The outer syntax of fact expressions (§3.3.9) involves theorems and attributes, which are evaluated in the context and applied to it. Attributes may declare theorems to the context, as in this_rule [intro] that_rule [elim] for example. Configuration options (§9.1) are special declaration attributes that operate on the context without a theorem, as in $[ [ s h o w \_ t y p e s = f a l s e ] ]$ for example. 

Expressions of this form may be defined as bundled declarations in the context, and included in other situations later on. Including declaration bundles augments a local context casually without logical dependencies, which is in contrast to locales and locale interpretation (§5.7). 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/70455af1b14af021a28e1d47829dd8437505d6f10c2f86ea7d5693c5225d9652.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/72df90a51da4ffd6877cebc4fe42d78fb0df035e8a6e7585d3686af7d9bb2b1c.jpg)


includes 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/65cf42424e4e1c4b1148bfbbf22c9cd6369f9398acb21b821c4e267fe1916de6.jpg)


opening 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/31bc50c1c784ecc9af99c84cb8c563c5b0fd1234ffa4e28422914dd652bf0c7f.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/be6def58a846f034bf5eae8b658196ea9c3c8c3611300b68af813c1c9e7935fe.jpg)


bundle $b = d e c l s$ defines a bundle of declarations in the current context. The RHS is similar to the one of the declare command. Bundles defined in local theory targets are subject to transformations via morphisms, when moved into different application contexts; this works analogously to any other local theory specification. 

bundle $b$ begin body end defines a bundle of declarations from the body of local theory specifications. It may consist of commands that are technically equivalent to declare or declaration, which also includes notation, for example. Named fact declarations like “lemmas a [simp] $= b ^ { , }$ or “lemma $a$ [simp]: B hproof i” are also admitted, but the name bindings are not recorded in the bundle. 

print_bundles prints the named bundles that are available in the current context; the “!” option indicates extra verbosity. 

include $b _ { 1 }$ . . . $b _ { n }$ activates the declarations from the given bundles in a proof body (forward mode). This is analogous to note (§6.2.3) with the expanded bundles. 

including $b _ { 1 }$ . . . $b _ { n }$ is similar to include, but works in proof refinement (backward mode). This is analogous to using (§6.2.3) with the expanded bundles. 

includes $b _ { 1 }$ . . . $b _ { n }$ is similar to include, but applies to a confined specification context: unnamed contexts and long statements of theorem. 

opening $b _ { 1 }$ . . . $b _ { n }$ is similar to includes, but applies to a named specification context: locales, classes and named contexts. The effect is confined to the surface context within the specification block itself and the corresponding begin / end block. 

unbundle $b _ { 1 }$ . . . $b _ { n }$ activates the declarations from the given bundles in the current local theory context. This is analogous to lemmas (§5.13) with the expanded bundles. 

Here is an artificial example of bundling various configuration options: 

bundle $t r a c e = [ [ s i m p \_ t r a c e$ , linarith_trace, metis_trace, smt_trace]] 

lemma $x = x$ 

including trace by metis 

# 5.4 Term definitions

definition : local_theory $\rightarrow$ local_theory  
defn : attribute  
print_defn_rule\* : context $\rightarrow$ abbreviation : local_theory $\rightarrow$ local_theory  
print_abbrevs\* : context $\rightarrow$ 

Term definitions may either happen within the logic (as equational axioms of a certain form (see also §5.9), or outside of it as rewrite system on abstract syntax. The second form is called “abbreviation”. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/dffe11d5ee2ac1e5b8cfef9b7c5bd79395920147a00226ca298bbb97a5c2458f.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/abc727112494cd4ad7b539f95e5072041b55a763db3f6944ea5611c4a18d6c3e.jpg)


decl 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/83046339f111f919cab939b7670c259ac6230b8e52591a1a2925fb97c25dc5a3.jpg)


definition 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/10bdc5c27535babd546d8c10b0479554ab34fb0d926d72aa1c51ccc91c987ec7.jpg)


abbreviation 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/95af716dd4016e5c835ffe8fbadb38bd9b84d22224c9080cd05806bf99a04cd1.jpg)


definition c where eq produces an internal definition $c \equiv t$ according to the specification given as eq, which is then turned into a proven fact. The given proposition may deviate from internal meta-level equality according to the rewrite rules declared as defn by the object-logic. This usually covers object-level equality $x = y$ and equivalence $A \longleftrightarrow$ $B$ . End-users normally need not change the defn setup. 

Definitions may be presented with explicit arguments on the LHS, as well as additional conditions, e.g. $f x y = t$ instead of $f \equiv \lambda x y$ . $t$ and $y \ne 0 \Longrightarrow g x y = u$ instead of an unrestricted $g \equiv \lambda x y$ . u. 

print_defn_rules prints the definitional rewrite rules declared via defn in the current context. 

abbreviation c where eq introduces a syntactic constant which is associated with a certain term according to the meta-level equality eq. 

Abbreviations participate in the usual type-inference process, but are expanded before the logic ever sees them. Pretty printing of terms involves higher-order rewriting with rules stemming from reverted abbreviations. This needs some care to avoid overlapping or looping syntactic replacements! 

The optional mode specification restricts output to a particular print mode; using “input” here achieves the effect of one-way abbreviations. The mode may also include an “output” qualifier that affects the concrete syntax declared for abbreviations, cf. syntax in §8.5.2. 

print_abbrevs prints all constant abbreviations of the current context; the “!” option indicates extra verbosity. 

# 5.5 Axiomatizations

axiomatization : theory → theory (axiomatic!) 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/46464f3276d46295556635d908796ab66ea840b9dbc4b8d5631389d192b475e6.jpg)


axiomatization 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5d414082d67adb24cd02ef542ab326e311dee75492aa60913c8978ad5ee9fde4.jpg)


axiomatization c1 . . . $c _ { m }$ where ϕ1 . . . $\varphi _ { n }$ introduces several constants simultaneously and states axiomatic properties for these. The constants are marked as being specified once and for all, which prevents additional specifications for the same constants later on, but it is always possible to emit axiomatizations without referring to particular constants. Note that lack of precise dependency tracking of axiomatizations may disrupt the well-formedness of an otherwise definitional theory. 

Axiomatization is restricted to a global theory context: support for local theory targets §5.2 would introduce an extra dimension of uncertainty what the written specifications really are, and make it infeasible to argue why they are correct. 

Axiomatic specifications are required when declaring a new logical system within Isabelle/Pure, but in an application environment like Isabelle/HOL the user normally stays within definitional mechanisms provided by the logic and its libraries. 

# 5.6 Generic declarations

declaration : local_theory $\rightarrow$ local_theory syntax_declaration : local_theory $\rightarrow$ local_theory declare : local_theory $\rightarrow$ local_theory 

Arbitrary operations on the background context may be wrapped-up as generic declaration elements. Since the underlying concept of local theories may be subject to later re-interpretation, there is an additional dependency on a morphism that tells the difference of the original declaration context wrt. the application context encountered later on. A fact declaration is an important special case: it consists of a theorem which is applied to the context by means of an attribute. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5c0dc23a51742fb5c79f49483f218192fb9c74fdbed0c3c1bc56f2e5c2ea836b.jpg)


declaration d adds the declaration function $d$ of ML type Morphism.declaration, to the current local theory under construction. In later application contexts, the function is transformed according to the morphisms being involved in the interpretation hierarchy. 

If the (pervasive) option is given, the corresponding declaration is applied to all possible contexts involved, including the global background theory. 

syntax_declaration is similar to declaration, but is meant to affect only “syntactic” tools by convention (such as notation and type-checking information). 

declare thms declares theorems to the current local theory context. No theorem binding is involved here, unlike lemmas (cf. §5.13), so declare 

only has the effect of applying attributes as included in the theorem specification. 

# 5.7 Locales

A locale is a functor that maps parameters (including implicit type parameters) and a specification to a list of declarations. The syntax of locales is modeled after the Isar proof context commands (cf. §6.2.1). 

Locale hierarchies are supported by maintaining a graph of dependencies between locale instances in the global theory. Dependencies may be introduced through import (where a locale is defined as sublocale of the imported instances) or by proving that an existing locale is a sublocale of one or several locale instances. 

A locale may be opened with the purpose of appending to its list of declarations (cf. §5.2). When opening a locale declarations from all dependencies are collected and are presented as a local theory. In this process, which is called roundup, redundant locale instances are omitted. A locale instance is redundant if it is subsumed by an instance encountered earlier. A more detailed description of this process is available elsewhere [4]. 

# 5.7.1 Locale expressions

A locale expression denotes a context composed of instances of existing locales. The context consists of the declaration elements from the locale instances. Redundant locale instances are omitted according to roundup. 

locale_expr 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9888543123478e2b680a96ae79b431547d0ed3e9a67dee4098d50fc5a8134dc2.jpg)


instance 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b96b3360cd755fb1b6b858cb0c5b49c5df815aaae7e9c8170039899a6d407737.jpg)


qualifier 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0ccc06d7166bd50a3df9b69842dd9186669e997ca33607defbef4aa2fab86456.jpg)


pos_insts 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/472f8d7e5d228fd67904b2fcc2f969acbb90d7333baddf9b483793d17b314ac1.jpg)


named_insts 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/8a3517c7b7f5848e2dabec59af3a87dea2f5ac8d30e56f8aacac987831d4e074.jpg)


rewrites 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/dfdbd5337641cc399457980493209c919b58bf302a114342efdc1628ef17aa06.jpg)


A locale instance consists of a reference to a locale and either positional or named parameter instantiations optionally followed by rewrites clauses. 

Identical instantiations (that is, those that instantiate a parameter by itself) may be omitted. The notation “_” enables to omit the instantiation for a parameter inside a positional instantiation. 

Terms in instantiations are from the context the locale expressions is declared in. Local names may be added to this context with the optional for clause. This is useful for shadowing names bound in outer contexts, and for declaring syntax. In addition, syntax declarations from one instance are effective when parsing subsequent instances of the same expression. 

Instances have an optional qualifier which applies to names in declarations. Names include local definitions and theorem names. If present, the qualifier itself is either mandatory (default) or non-mandatory (when followed by “?”). Non-mandatory means that the qualifier may be omitted on input. Qualifiers only affect name spaces; they play no role in determining whether one locale instance subsumes another. 

Rewrite clauses amend instances with equations that act as rewrite rules. This is particularly useful for changing concepts introduced through definitions. Rewrite clauses are available only in interpretation commands (see §5.7.3 below) and must be proved the user. 

# 5.7.2 Locale declarations

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2542e74b937f2b8b6d5817bddd0c48bd065b3a8be5222e71bc6428fa63c84cb0.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/59f6288ba0139ab90095daf94673492b440512c5a0c2ee2e746013d273591a7a.jpg)


locale 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/8dc1f28c20e7924e9bf6dd76859f95f1bfde0a27466291adc9523f0c18638850.jpg)


context_elem 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d136a40d49ce6b839e8bbd8716f59f6853fd6623fa0e7cb9a86c3bfcf887b6cb.jpg)


locale loc = import opening bundles $^ +$ body defines a new locale loc as a context consisting of a certain view of existing locales (import) plus some additional elements (body) with declaration bundles enriching the context of the command itself. All import, bundles and body are optional; the degenerate form locale loc defines an empty locale, which may still be useful to collect declarations of facts later on. Typeinference on locale expressions automatically takes care of the most general typing that the combined context elements may acquire. 

The import consists of a locale expression; see §5.7.1 above. Its for clause defines the parameters of import. These are parameters of the defined locale. Locale parameters whose instantiation is omitted automatically extend the (possibly empty) for clause: they are inserted at its beginning. This means that these parameters may be referred to from within the expression and also in the subsequent context elements and provides a notational convenience for the inheritance of parameters in locale declarations. 

Declarations from bundles, see §5.3, are effective in the entire command including a subsequent begin / end block, but they do not contribute to the declarations stored in the locale. 

The body consists of context elements: 

fixes x :: τ (mx) declares a local parameter of type $\tau$ and mixfix annotation $m x$ (both are optional). The special syntax declaration “(structure)” means that $x$ may be referenced implicitly in this context. 

constrains $x : : \tau$ introduces a type constraint $\tau$ on the local parameter $x$ . This element is deprecated. The type constraint should be introduced in the for clause or the relevant fixes element. 

assumes $a \colon \varphi _ { 1 } \ldots \varphi _ { n }$ $\varphi _ { n }$ introduces local premises, similar to assume within a proof (cf. §6.2.1). 

defines $a$ : $x \equiv t$ defines a previously declared parameter. This is similar to define within a proof (cf. §6.2.1), but defines is restricted to Pure equalities and the defined variable needs to be declared beforehand via fixes. The left-hand side of the equation may have additional arguments, e.g. “defines f x1 . . . $x _ { n } \equiv t ^ { \prime }$ , which need to be free in the context. 

notes $a = b _ { 1 }$ . . . $b _ { n }$ reconsiders facts within a local context. Most notably, this may include arbitrary declarations in any attribute specifications included here, e.g. a local simp rule. 

Both assumes and defines elements contribute to the locale specification. When defining an operation derived from the parameters, definition (§5.4) is usually more appropriate. 

Note that “(is $p _ { 1 } \ldots p _ { n } ,$ )” patterns given in the syntax of assumes and defines above are illegal in locale definitions. In the long goal format of §6.2.4, term bindings may be included as expected, though. 

Locale specifications are “closed up” by turning the given text into a predicate definition loc_axioms and deriving the original assumptions as local lemmas (modulo local definitions). The predicate statement covers only the newly specified assumptions, omitting the content of included locale expressions. The full cumulative view is only provided on export, involving another predicate loc that refers to the complete specification text. 

In any case, the predicate arguments are those locale parameters that actually occur in the respective piece of text. Also these predicates operate at the meta-level in theory, but the locale packages attempts to internalize statements according to the object-logic setup (e.g. replacing $\Lambda$ by $\forall$ , and =⇒ by −→ in HOL; see also §9.5). Separate introduction rules loc_axioms.intro and loc.intro are provided as well. 

experiment body begin opens an anonymous locale context with private naming policy. Specifications in its body are inaccessible from outside. This is useful to perform experiments, without polluting the name space. 

print_locale locale prints the contents of the named locale. The command omits notes elements by default. Use print_locale! to have them included. 

print_locales prints the names of all locales of the current theory; the “!” option indicates extra verbosity. 

locale_deps visualizes all locales and their relations as a Hasse diagram. This includes locales defined as type classes (§5.8). 

# 5.7.3 Locale interpretation

interpretation : local_theory $\rightarrow$ proof(prove)  
interpret : proof(state) | proof(chain) $\rightarrow$ proof(prove)  
global Interpretation : theory | local_theory $\rightarrow$ proof(prove)  
sublocale : theory | local_theory $\rightarrow$ proof(prove)  
print_interps* : context $\rightarrow$ intro locales : method  
unfold locales : method  
trace locales : attribute default false 

Locales may be instantiated, and the resulting instantiated declarations added to the current context. This requires proof (of the instantiated specification) and is called locale interpretation. Interpretation is possible within arbitrary local theories (interpretation), within proof bodies (interpret), into global theories (global_interpretation) and into locales (sublocale). 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e297833edfbb58c899d22b66f18861b7e34c561604855b065d99dcf60abc303d.jpg)


The core of each interpretation command is a locale expression expr; the command generates proof obligations for the instantiated specifications. Once these are discharged by the user, instantiated declarations (in particular, facts) are added to the context in a post-processing phase, in a manner specific to each command. 

Interpretation commands are aware of interpretations that are already active: post-processing is achieved through a variant of roundup that takes interpretations of the current global or local theory into account. In order to simplify the proof obligations according to existing interpretations use methods intro_locales or unfold_locales. 

Rewrites clauses rewrites eqns occur within expressions. They amend the morphism through which a locale instance is interpreted with rewrite rules, also called rewrite morphisms. This is particularly useful for interpreting concepts introduced through definitions. The equations must be proved the user. To enable syntax of the instantiated locale within the equation, while reading a locale expression, equations of a locale instance are read in a temporary context where the instance is already activated. If activation fails, typically due to duplicate constant declarations, processing falls back to reading the equation first. 

Given definitions defs produce corresponding definitions in the local theory’s underlying target and amend the morphism with rewrite rules stemming from the symmetric of those definitions. Hence these need not be proved explicitly the user. Such rewrite definitions are a even more useful device for interpreting concepts introduced through definitions, but they are only supported for interpretation commands operating in a local theory whose implementing target actually supports this. Note that despite the suggestive and connective, defs are processed sequentially without mutual recursion. 

interpretation expr interprets expr into a local theory such that its lifetime is limited to the current context block (e.g. a locale or unnamed context). At the closing end of the block the interpretation and its declarations disappear. Hence facts based on interpretation can be established without creating permanent links to the interpreted locale instances, as would be the case with sublocale. 

When used on the level of a global theory, there is no end of a current context block, hence interpretation behaves identically to global_interpretation then. 

interpret expr interprets expr into a proof context: the interpretation and its declarations disappear when closing the current proof block. Note that for interpret the eqns should be explicitly universally quantified. 

global_interpretation expr defines defs interprets expr into a global theory. 

When adding declarations to locales, interpreted versions of these declarations are added to the global theory for all interpretations in the 

global theory as well. That is, interpretations into global theories dynamically participate in any declarations added to locales. 

Free variables in the interpreted expression are allowed. They are turned into schematic variables in the generated declarations. In order to use a free variable whose name is already bound in the context — for example, because a constant of that name exists — add it to the for clause. 

When used in a nested target, resulting declarations are propagated through the whole target stack. 

sublocale name ⊆ expr defines defs interprets expr into the locale name. 

A proof that the specification of name implies the specification of expr is required. As in the localized version of the theorem command, the proof is in the context of name. After the proof obligation has been discharged, the locale hierarchy is changed as if name imported expr (hence the name sublocale). When the context of name is subsequently entered, traversing the locale hierarchy will involve the locale instances of expr, and their declarations will be added to the context. This makes sublocale dynamic: extensions of a locale that is instantiated in expr may take place after the sublocale declaration and still become available in the context. Circular sublocale declarations are allowed as long as they do not lead to infinite chains. 

If interpretations of name exist in the current global theory, the command adds interpretations for expr as well, with the same qualifier, although only for fragments of expr that are not interpreted in the theory already. 

Rewrites clauses in the expression or rewrite definitions defs can help break infinite chains induced by circular sublocale declarations. 

In a named context block the sublocale command may also be used, but the locale argument must be omitted. The command then refers to the locale (or class) target of the context block. 

print_interps name lists all interpretations of locale name in the current theory or proof context, including those due to a combination of an interpretation or interpret and one or several sublocale declarations. 

intro_locales and unfold_locales repeatedly expand all introduction rules of locale predicates of the theory. While intro_locales only applies the loc.intro introduction rules and therefore does not descend to assumptions, unfold_locales is more aggressive and applies loc_axioms.intro 

as well. Both methods are aware of locale specifications entailed by the context, both from target statements, and from interpretations (see below). New goals that are entailed by the current context are discharged automatically. 

While unfold_locales is part of the default method for proof and often invoked “behind the scenes”, intro_locales helps understand which proof obligations originated from which locale instances. The latter method is useful while developing proofs but rare in finished developments. 

trace_locales, when set to true, prints the locale instances activated during roundup. Use this when locale commands yield obscure errors or for understanding local theories created by complex locale hierarchies. 

! If a global theory inherits declarations (body elements) for a locale from • one parent and an interpretation of that locale from another parent, the interpretation will not be applied to the declarations. 

! Since attributes are applied to interpreted theorems, interpretation may : modify the context of common proof tools, e.g. the Simplifier or Classical Reasoner. As the behaviour of such tools is not stable under interpretation morphisms, manual declarations might have to be added to the target context of the interpretation to revert such declarations. 

! An interpretation in a local theory or proof context may subsume previ-: ous interpretations. This happens if the same specification fragment is interpreted twice and the instantiation of the second interpretation is more general than the interpretation of the first. The locale package does not attempt to remove subsumed interpretations. 

While interpretation (in c) . . . is admissible, it is not useful since its result : is discarded immediately. 

# 5.8 Classes

class : theory $\rightarrow$ local_theory  
instantiation : theory $\rightarrow$ local_theory  
instance : local_theory $\rightarrow$ local_theory  
instance : theory $\rightarrow$ proof(prove)  
subclass : local_theory $\rightarrow$ local_theory  
print_classes\* : context $\rightarrow$ class_deps\* : context $\rightarrow$ intro_classes : method 

A class is a particular locale with exactly one type variable $\alpha$ . Beyond the underlying locale, a corresponding type class is established which is interpreted logically as axiomatic type class [57] whose logical content are the assumptions of the locale. Thus, classes provide the full generality of locales combined with the commodity of type classes (notably type-inference). See [22] for a short tutorial. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/470d0ebcc5a23e3bb8b1073dd4ad50be28879f2deffc0bfec9072c90d697f8b2.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1322550a9a1579a00dd9435ce3914fcf42b561a7ed380659adf6130c50c8a903.jpg)


class_bounds 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d0b45102def45ea7cec5f306616f71ea02e99b33d67ad18e9a943bacbad4cb93.jpg)


class c = superclasses bundles $^ +$ body defines a new class $c$ , inheriting from superclasses. This introduces a locale $c$ with import of all locales superclasses. 

Any fixes in body are lifted to the global theory level (class operations $f _ { 1 }$ , . . . , $f _ { n }$ of class $c$ ), mapping the local type parameter $\alpha$ to a schematic type variable ? $\ell \alpha : : \boldsymbol { c }$ . 

Likewise, assumes in body are also lifted, mapping each local parameter $f : : \tau [ \alpha ]$ to its corresponding global constant $f : \tau [ \mathscr { \ ? } \alpha : : c ]$ . The corresponding introduction rule is provided as c_class_axioms.intro. This rule should be rarely needed directly — the intro_classes method takes care of the details of class membership proofs. 

Optionally given bundles take effect in the surface context within the body and the potentially following begin / end block. 

instantiation $t : ( s _ { 1 } , \ldots , s _ { n } ) s$ begin opens a target (cf. §5.2) which allows to specify class operations $f _ { 1 }$ , . . . , $f _ { n }$ corresponding to sort $s$ at the particular type instance (α1 :: s1, . . . , $\alpha _ { n } \ : \because \ s _ { n }$ ) $t$ . A plain instance command in the target body poses a goal stating these type arities. The target is concluded by an end command. 

Note that a list of simultaneous type constructors may be given; this corresponds nicely to mutually recursive type definitions, e.g. in Isabelle/HOL. 

instance in an instantiation target body sets up a goal stating the type arities claimed at the opening instantiation. The proof would usually proceed by intro_classes, and then establish the characteristic theorems of the type classes involved. After finishing the proof, the background theory will be augmented by the proven type arities. 

On the theory level, instance $t : ( s _ { 1 } , \ldots , s _ { n } ) s$ provides a convenient way to instantiate a type class with no need to specify operations: one can continue with the instantiation proof immediately. 

subclass $c$ in a class context for class $d$ sets up a goal stating that class $c$ is logically contained in class $d$ . After finishing the proof, class $d$ is proven to be subclass $c$ and the locale $c$ is interpreted into $d$ simultaneously. 

A weakened form of this is available through a further variant of instance: instance $c _ { 1 } \subseteq c _ { 2 }$ opens a proof that class $c _ { 2 }$ implies $c _ { 1 }$ without reference to the underlying locales; this is useful if the properties to prove the logical connection are not sufficient on the locale level but on the theory level. 

print_classes prints all classes in the current theory. 

class_deps visualizes classes and their subclass relations as a directed acyclic graph. By default, all classes from the current theory context are show. This may be restricted by optional bounds as follows: class_deps upper or class_deps upper lower. A class is visualized, iff it is a subclass of some sort from upper and a superclass of some sort from lower. 

intro_classes repeatedly expands all class introduction rules of this theory. Note that this method usually needs not be named explicitly, as it is already included in the default proof step (e.g. of proof ). In particular, instantiation of trivial (syntactic) classes may be performed by a single “..” proof step. 

# 5.8.1 The class target

A named context may refer to a locale (cf. §5.2). If this locale is also a class $c$ , apart from the common locale target behaviour the following happens. 

• Local constant declarations $g [ \alpha ]$ referring to the local type parameter $\alpha$ and local parameters $f [ \alpha ]$ are accompanied by theory-level constants $g [ \mathcal { 2 } \alpha : \cdot ~ c ]$ referring to theory-level class operations $f [ \mathcal { 2 } \alpha : \mathfrak { c } ]$ . 

• Local theorem bindings are lifted as are assumptions. 

• Local syntax refers to local operations $g [ \alpha ]$ and global operations $g [ \mathcal { Q } \alpha$ :: c] uniformly. Type inference resolves ambiguities. In rare cases, manual type annotations are needed. 

# 5.8.2 Co-regularity of type classes and arities

The class relation together with the collection of type-constructor arities must obey the principle of co-regularity as defined below. 

For the subsequent formulation of co-regularity we assume that the class relation is closed by transitivity and reflexivity. Moreover the collection of arities $t : ( \overline { { s } } ) c$ is completed such that $t : ( \overline { { s } } ) c$ and $c \subseteq c ^ { \prime }$ implies $t : ( \overline { { s } } ) c ^ { \prime }$ for all such declarations. 

Treating sorts as finite sets of classes (meaning the intersection), the class relation $c _ { 1 } \subseteq c _ { 2 }$ is extended to sorts as follows: 

$$
s _ {1} \subseteq s _ {2} \equiv \forall c _ {2} \in s _ {2}. \exists c _ {1} \in s _ {1}. c _ {1} \subseteq c _ {2}
$$

This relation on sorts is further extended to tuples of sorts (of the same length) in the component-wise way. 

Co-regularity of the class relation together with the arities relation means: 

$$
t: \left(\bar {s} _ {1}\right) c _ {1} \Longrightarrow t: \left(\bar {s} _ {2}\right) c _ {2} \Longrightarrow c _ {1} \subseteq c _ {2} \Longrightarrow \bar {s} _ {1} \subseteq \bar {s} _ {2}
$$

for all such arities. In other words, whenever the result classes of some typeconstructor arities are related, then the argument sorts need to be related in the same way. 

Co-regularity is a very fundamental property of the order-sorted algebra of types. For example, it entails principal types and most general unifiers, e.g. see [40]. 

# 5.9 Overloaded constant definitions

Definitions essentially express abbreviations within the logic. The simplest form of a definition is $c : \sigma \equiv t$ , where $c$ is a new constant and $t$ is a closed term that does not mention $c$ . Moreover, so-called hidden polymorphism is excluded: all type variables in $t$ need to occur in its type $\sigma$ . 

Overloading means that a constant being declared as $c : : \alpha$ decl may be defined separately on type instances $c : ( \beta _ { 1 } , \ldots , \beta _ { n } ) \kappa$ decl for each type constructor $\kappa$ . At most occasions overloading will be used in a Haskell-like fashion together with type classes by means of instantiation (see §5.8). Sometimes low-level overloading is desirable; this is supported by consts and overloading explained below. 

The right-hand side of overloaded definitions may mention overloaded constants recursively at type instances corresponding to the immediate argument types $\beta _ { 1 }$ , . . . , $\beta _ { n }$ . Incomplete specification patterns impose global constraints on all occurrences. E.g. $d : : \alpha \times \alpha$ on the left-hand side means that all corresponding occurrences on some right-hand side need to be an instance of this, and general $d : : \alpha \times \beta$ will be disallowed. Full details are given by Kunčar [27]. 

The consts command and the overloading target provide a convenient interface for end-users. Regular specification elements such as definition, inductive, function may be used in the body. It is also possible to use consts $c : : \sigma$ with later overloading $c = c : \sigma$ to keep the declaration and definition of a constant separate. 

$\begin{array}{rl}\mathbf{consts} & :\text{theory}\to \text{theory}\\ \mathbf{overloading} & :\text{theory}\to \mathbf{local\_theory} \end{array}$ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0a15bcd5956a5901697227cd4fd8b0a6de1b0541ee14c4bea876c6d9dd87a79b.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/cededfab2262dace968e663985337679460da1f4c14850885bd5c29dfee5fb3a.jpg)


spec 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e125a8f39e74cce3be35552848bce0a95914288168fcd3e5b18b7f7a16c8f57f.jpg)


consts $c : : \sigma$ declares constant $c$ to have any instance of type scheme $\sigma$ . The optional mixfix annotations may attach concrete syntax to the constants declared. 

overloading $x _ { 1 } \equiv c _ { 1 } : : \tau _ { 1 } \ . . . \ x _ { n } \equiv c _ { n } : : \tau _ { n }$ $x _ { n } \equiv c _ { n } : : \tau _ { n }$ begin . . . end defines a theory target (cf. §5.2) which allows to specify already declared constants via definitions in the body. These are identified by an explicitly given mapping from variable names $x _ { i }$ to constants $c _ { i }$ at particular type instances. The definitions themselves are established using common specification tools, using the names $x _ { i }$ as reference to the corresponding constants. 

Option (unchecked) disables global dependency checks for the corresponding definition, which is occasionally useful for exotic overloading; this is a form of axiomatic specification. It is at the discretion of the user to avoid malformed theory specifications! 

# Example

consts Length :: 0a ⇒ nat 

# overloading

Length0 ≡ Length :: unit ⇒ nat 

Length1 ≡ Length :: 0a × unit ⇒ nat 

Length2 ≡ Length :: 0a × 0b × unit ⇒ nat 

Length3 ≡ Length :: 0a × 0b × 0c × unit ⇒ nat 

fun Length0 :: unit $\Rightarrow$ nat where Length0 $( ) = 0$ 

fun Length1 :: 0a × unit ⇒ nat where Length1 $( a , ( ) ) = 1$ 

fun Length2 :: ${ \mathit { \ ' } a \mathrm { \times } } \mathit { \prime } b \mathrm { \times } \mathit { u n i t } \Rightarrow \mathit { n c }$ t where Length2 $( a , b , ( ) ) = 2$ 

fun Length3 :: ${ \bf \langle } a \mathrm { ~ \times ~ } ^ { \prime } b \mathrm { ~ \times ~ } ^ { \prime } c \mathrm { ~ \times ~ } u n i t \Rightarrow n a t$ where Length3 $( a , b , c , ( ) ) = 3$ 

end 

lemma Length $( a , \ b , \ c , \ ( ) ) = 3$ by simp 

lemma Length $( ( a , b ) , ( c , d ) , ( ) ) = 2$ by simp 

lemma Length $( ( a , \ b , \ c , \ d , \ e ) , \ ( ) ) = 1$ by simp 

# 5.10 Incorporating ML code

SML_file : local_theory local_theory 

SML_file_debug : local_theory local_theory 

SML_file_no_debug : local_theory local_theory 

ML_file : local_theory local_theory 

ML_file_debug : local_theory local_theory 

ML_file_no_debug : local_theory local_theory 

ML : local_theory local_theory 

ML_export : local_theory local_theory 

ML_prf : proof proof 

ML_val : any → 

ML_command : any → 

setup : theory → theory 

local_setup : local_theory → local_theory 

attribute_setup : local_theory → local_theory 

ML_print_depth : attribute default 10 

ML_source_trace : attribute default false 

ML_debugger : attribute default false 

ML_exception_trace : attribute default false 

ML_exception_debugger : attribute default false 

ML_environment : attribute default Isabelle 

SML_file 

SML_file_debug 

SML_file_no_debug 

ML_file 

ML_file_debug 

ML_file_no_debug 

name 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/03d9510a9a9eb7f597f1f2f61dd6a1ef97af98b63330015f38fcc0a0569f331c.jpg)


SML_file name reads and evaluates the given Standard ML file. Top-level SML bindings are stored within the (global or local) theory context; the initial environment is restricted to the Standard ML implementation of Poly/ML, without the many add-ons of Isabelle/ML. Multiple SML_file commands may be used to build larger Standard ML projects, independently of the regular Isabelle/ML environment. 

ML_file name reads and evaluates the given ML file. The current theory context is passed down to the ML toplevel and may be modified, using Context.>> or derived ML commands. Top-level ML bindings are stored within the (global or local) theory context. 

SML_file_debug, SML_file_no_debug, ML_file_debug, and ML_file_no_debug change the ML_debugger option locally while the given file is compiled. 

ML is similar to ML_file, but evaluates directly the given text. Top-level ML bindings are stored within the (global or local) theory context. 

ML_export is similar to ML, but the resulting toplevel bindings are exported to the global bootstrap environment of the ML process — it has a lasting effect that cannot be retracted. This allows ML evaluation without a formal theory context, e.g. for command-line tools via isabelle process [54]. 

ML_prf is analogous to ML but works within a proof context. Top-level ML bindings are stored within the proof context in a purely sequential fashion, disregarding the nested proof structure. ML bindings introduced by ML_prf are discarded at the end of the proof. 

ML_val and ML_command are diagnostic versions of ML, which means that the context may not be updated. ML_val echos the bindings produced at the ML toplevel, but ML_command is silent. 

setup text changes the current theory context by applying text, which refers to an ML expression of type theory -> theory. This enables to initialize any object-logic specific tools and packages written in ML, for example. 

local_setup is similar to setup for a local theory context, and an ML expression of type local_theory -> local_theory. This allows to invoke local theory specification packages without going through concrete outer syntax, for example. 

attribute_setup name = text description defines an attribute in the current context. The given text has to be an ML expression of type attribute context_parser, cf. basic parsers defined in structure Args and Attrib. 

In principle, attributes can operate both on a given theorem and the implicit context, although in practice only one is modified and the other serves as parameter. Here are examples for these two cases: 

attribute_setup my_rule = <Attrib.thms >> (fnths => Thm.rule_attributeths (fn context:Context.Generic $\Rightarrow$ fn th:thm $=$ let val th' $\equiv$ th OFths in th' end))>   
attribute_setup my_declaration $=$ <Attrib.thms $>>$ (fnths $\Longrightarrow$ Thm.declaration_attribute (fn th:thm $\Longrightarrow$ fn context:Context.generic $\Longrightarrow$ let val context' $\equiv$ context in context' end))> 

ML_print_depth controls the printing depth of the ML toplevel pretty printer. Typically the limit should be less than 10. Bigger values such as 100–1000 are occasionally useful for debugging. 

ML_source_trace indicates whether the source text that is given to the ML compiler should be output: it shows the raw Standard ML after expansion of Isabelle/ML antiquotations. 

ML_debugger controls compilation of sources with or without debugging information. The global system option ML_debugger does the same when building a session image. It is also possible use commands like ML_file_debug etc. The ML debugger is explained further in [56]. 

ML_exception_trace indicates whether the ML run-time system should print a detailed stack trace on exceptions. The result is dependent on various ML compiler optimizations. The boundary for the exception trace is the current Isar command transactions: it is occasionally better to insert the combinator Runtime.exn_trace into ML code for debugging [55], closer to the point where it actually happens. 

ML_exception_debugger controls detailed exception trace via the Poly/ML debugger, at the cost of extra compile-time and run-time overhead. Relevant ML modules need to be compiled beforehand with debugging enabled, see ML_debugger above. 

ML_environment determines the named ML environment for toplevel declarations, e.g. in command ML or ML_file. The following ML environments are predefined in Isabelle/Pure: 

• Isabelle for Isabelle/ML. It contains all modules of Isabelle/Pure and further add-ons, e.g. material from Isabelle/HOL. 

• SML for official Standard ML. It contains only the initial basis according to http://sml-family.org/Basis/overview.html. 

The Isabelle/ML function ML_Env.setup defines a new ML environment. This is useful to incorporate big SML projects in an isolated name space, possibly with variations on ML syntax; the existing setup of ML_Env.SML_operations follows the official standard. 

It is also possible to move toplevel bindings between ML environments, using a notation with “>” as separator. For example: 

declare [[ML_environment = Isabelle>SML]] 

ML ‹val println $=$ writeln› 

declare $[ [ M L \_ e n v i r o n m e n t = S M L ] ]$ 

ML ‹println "test"› 

declare [[ML_environment = Isabelle]] 

ML ‹ML ‹println› (*bad*) handle ERROR msg => warning msg› 

# 5.11 Generated files and exported files

Write access to the physical file-system is incompatible with the stateless model of processing Isabelle documents. To avoid bad effects, the following concepts for abstract file-management are provided by Isabelle: 

Generated files are stored within the theory context in Isabelle/ML. This allows to operate on the content in Isabelle/ML, e.g. via the command compile_generated_files. 

Exported files are stored within the session database in Isabelle/Scala. This allows to deliver artefacts to external tools, see also [54] for session ROOT declaration export_files, and isabelle build option -e. 

A notable example is the command export_code (chapter 13): it uses both concepts simultaneously. 

File names are hierarchically structured, using a slash as separator. The (long) theory name is used as a prefix: the resulting name needs to be globally unique. 

generate_file : local_theory $\longrightarrow$ local_theory 

export_generated_files : context → 

compile_generated_files : context → 

external_file : any → any 

generate_file 

path 

content 

path 

embedded 

content 

embedded 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/66a67dcfdf4827254166f5d540eb8321d57c37126dc1a4fea334c398492eed9e.jpg)


files_in_theory 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e933c5011f79c5487e5849fe620fdb03acb51b43d9289930163a538ca4492db7.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d01582933d6a4a31728347bb8362d350272ea23e474da374bb1d303025fe895d.jpg)


external_files 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4a461b38acf4ac29ecb0e839ee4caca607d68411fdd421759f3c62c34e0cead9.jpg)


export_files 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/abb8227175fda7fdff465a739228d714a98b6b631ae3a3a2a512ade7fddeecfc.jpg)


executable 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4db077e593193c87925b68c542706b4ee6fdbf0fc79245fa1e77be847c733f5f.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/391c0de199558deeccff0e2f0dd9d13fcbc7de1dc5318919820b75221b63f8fc.jpg)


generate_file $p a t h = c o n t e n t$ augments the table of generated files within the current theory by a new entry: duplicates are not allowed. The name extension determines a pre-existent file-type; the content is a string that is preprocessed according to rules of this file-type. 

For example, Isabelle/Pure supports .hs as file-type for Haskell: embedded cartouches are evaluated as Isabelle/ML expressions of type string, the result is inlined in Haskell string syntax. 

export_generated_files paths (in thy) retrieves named generated files from the given theory (that needs be reachable via imports of the current one). By default, the current theory node is used. Using “_” (underscore) instead of explicit path names refers to all files of a theory node. 

The overall list of files is prefixed with the respective (long) theory name and exported to the session database. In Isabelle/jEdit the result can be browsed via the virtual file-system with prefix “isabelle-export:” (using the regular file-browser). 

scala_build_generated_files paths (in thy) retrieves named generated files as for export_generated_files and writes them into a temporary directory, which is taken as starting point for build process of Isabelle/Scala/Java modules (see [54]). The corresponding build.props file is expected directly in the toplevel directory, instead of etc/build.props for Isabelle system components. These properties need to specify sources, resources, services etc. as usual. The resulting JAR module becomes an export artefact of the session database, with a name of the form “theory:classpath/module.jar”. 

compile_generated_files paths (in thy) where compile_body retrieves named generated files as for export_generated_files and writes them into a temporary directory, such that the compile_body may operate on them as an ML function of type Path.T -> unit. This may create further files, e.g. executables produced by a compiler that is invoked as external process (e.g. via Isabelle_System.bash), or any other files. 

The option “external_files paths (in base_dir)” copies files from the physical file-system into the temporary directory, before invoking compile_body. The base_dir prefix is removed from each of the paths, but the remaining sub-directory structure is reconstructed in the target directory. 

The option “export_files paths” exports the specified files from the temporary directory to the session database, after invoking compile_body. Entries may be decorated with “(exe)” to say that it is a platform-specific executable program: the executable file-attribute will be set, and on Windows the .exe file-extension will be included; “(executable)” only refers to the file-attribute, without special treatment of the .exe extension. 

The option “export_prefix path” specifies an extra path prefix for all exports of export_files above. 

external_file name declares the formal dependency on the given file name, such that the Isabelle build process knows about it (see also [54]). This is required for any files mentioned in compile_generated_files / external_files above, in order to document source dependencies properly. It is also possible to use external_file alone, e.g. when other Isabelle/ML tools use File.read, without specific management of content by the Prover IDE. 

# 5.12 Primitive specification elements

# 5.12.1 Sorts

default_sort : local_theory → local_theory 

default_sort sort 

default_sort $s$ makes sort $s$ the new default sort for any type variable that is given explicitly in the text, but lacks a sort constraint (wrt. the current context). Type variables generated by type inference are not affected. 

Usually the default sort is only changed when defining a new objectlogic. For example, the default sort in Isabelle/HOL is type, the class of all HOL types. 

When merging theories, the default sorts of the parents are logically intersected, i.e. the representations as lists of classes are joined. 

# 5.12.2 Types

type.synonym : local_theory $\rightarrow$ local_theory typedefecl : local_theory $\rightarrow$ local_theory 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9568435cd9a3620a45b44ff63944837b8a12eb5cec2b1e0a14d4efe86be7064e.jpg)


type_synonym (α1, . . . , αn) $t = \tau$ introduces a type synonym $( \alpha _ { 1 } , \ldots ,$ $\alpha _ { n }$ ) $t$ for the existing type $\tau$ . Unlike the semantic type definitions in Isabelle/HOL, type synonyms are merely syntactic abbreviations without any logical significance. Internally, type synonyms are fully expanded. 

typedecl $\left( \alpha _ { 1 } , \ldots , \alpha _ { n } \right)$ $t$ declares a new type constructor $t$ . If the objectlogic defines a base sort $s$ , then the constructor is declared to operate on that, via the axiomatic type-class instance $t : ( s , \ldots , s ) s$ . 

! If you introduce a new type axiomatically, i.e. via typedecl and • axiomatization (§5.5), the minimum requirement is that it has a non-empty model, to avoid immediate collapse of the logical environment. Moreover, one needs to demonstrate that the interpretation of such free-form axiomatizations can coexist with other axiomatization schemes for types, notably typedef in Isabelle/HOL (§11.7), or any other extension that people might have introduced elsewhere. 

# 5.13 Naming existing theorems

lemmas : local_theory → local_theory named_theorems : local_theory → local_theory 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/56f44d76e3d091c7609c018f8a94eb8c40f08fc0cc44e72b422ad8776dbfd8dd.jpg)


lemmas $a = b _ { 1 }$ . . . $b _ { n }$ for $x _ { 1 }$ . . . $x _ { m }$ evaluates given facts (with attributes) in the current context, which may be augmented by local variables. Results are standardized before being stored, i.e. schematic variables are renamed to enforce index 0 uniformly. 

named_theorems name description declares a dynamic fact within the context. The same name is used to define an attribute with the usual add/del syntax (e.g. see §9.3.2) to maintain the content incrementally, in canonical declaration order of the text structure. 

# 5.14 Oracles

oracle : theory $\rightarrow$ theory (axiomatic!)  
thm_oracles* : context $\rightarrow$ 

Oracles allow Isabelle to take advantage of external reasoners such as arithmetic decision procedures, model checkers, fast tautology checkers or computer algebra systems. Invoked as an oracle, an external reasoner can create arbitrary Isabelle theorems. 

It is the responsibility of the user to ensure that the external reasoner is as trustworthy as the application requires. Another typical source of errors is the linkup between Isabelle and the external tool, not just its concrete implementation, but also the required translation between two different logical environments. 

Isabelle merely guarantees well-formedness of the propositions being asserted, and records within the internal derivation object how presumed theorems depend on unproven suppositions. This also includes implicit type-class reasoning via the order-sorted algebra of class relations and type arities (see also instantiation and instance). 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/32b3e3b57b42d03f30875a1731c135e70d86aa496899bd9970cb587d34c91828.jpg)


oracle $n a m e = t e x t$ turns the given ML expression text of type ’a -> cterm into an ML function of type ’a -> thm, which is bound to the global identifier name. This acts like an infinitary specification of axioms! Invoking the oracle only works within the scope of the resulting theory. 

See ~~/src/HOL/Examples/Iff_Oracle.thy for a worked example of defining a new primitive rule as oracle, and turning it into a proof method. 

thm_oracles thms displays all oracles used in the internal derivation of the given theorems; this covers the full graph of transitive dependencies. 

# 5.15 Name spaces

alias : local_theory local_theory 

type_alias : local_theory local_theory 

hide_class : theory theory 

hide_type : theory theory 

hide_const : theory theory 

hide_fact : theory theory 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fa3146b6cf26e8e41889c028e0fc16af2db6be9f79497e1a0be0971f5db0ce83.jpg)


Isabelle organizes any kind of name declarations (of types, constants, theorems etc.) by separate hierarchically structured name spaces. Normally the user does not have to control the behaviour of name spaces by hand, yet the following commands provide some way to do so. 

alias and type_alias introduce aliases for constants and type constructors, respectively. This allows adhoc changes to name-space accesses. 

type_alias $b = c$ introduces an alias for an existing type constructor. 

hide_class names fully removes class declarations from a given name space; with the (open) option, only the unqualified base name is hidden. 

Note that hiding name space accesses has no impact on logical declarations — they remain valid internally. Entities that are no longer accessible to the user are printed with the special qualifier “??” prefixed to the full internal name. 

hide_type, hide_const, and hide_fact are similar to hide_class, but hide types, constants, and facts, respectively. 

# Proofs

Proof commands perform transitions of Isar/VM machine configurations, which are block-structured, consisting of a stack of nodes with three main components: logical proof context, current facts, and open goals. Isar/VM transitions are typed according to the following three different modes of operation: 

proof (prove) means that a new goal has just been stated that is now to be proven; the next command may refine it by some proof method, and enter a sub-proof to establish the actual result. 

proof (state) is like a nested theory mode: the context may be augmented by stating additional assumptions, intermediate results etc. 

$p r o o f ( c h a i n )$ is intermediate between proof (state) and proof (prove): existing facts (i.e. the contents of the special this register) have been just picked up in order to be used when refining the goal claimed next. 

The proof mode indicator may be understood as an instruction to the writer, telling what kind of operation may be performed next. The corresponding typings of proof commands restricts the shape of well-formed proof texts to particular command sequences. So dynamic arrangements of commands eventually turn out as static texts of a certain structure. 

Appendix A gives a simplified grammar of the (extensible) language emerging that way from the different types of proof commands. The main ideas of the overall Isar framework are explained in chapter 2. 

# 6.1 Proof structure

# 6.1.1 Formal notepad

notepad : local_theory → proof (state) 

notepad begin 

end 

notepad begin opens a proof state without any goal statement. This allows to experiment with Isar, without producing any persistent result. The notepad is closed by end. 

# 6.1.2 Blocks

next : proo $f ( s t a t e ) \to p r o o f ( s t a t e )$ 

$\begin{array} { r } { \{ \begin{array} { c c c } { { } : } & { { p r o o f ( s t a t e )  p r o o f ( s t a t e ) } } \end{array}  } \end{array}$ 

} $: \ p r o o f ( s t a t e ) \to p r o o f ( s t a t e )$ 

While Isar is inherently block-structured, opening and closing blocks is mostly handled rather casually, with little explicit user-intervention. Any local goal statement automatically opens two internal blocks, which are closed again when concluding the sub-proof (by qed etc.). Sections of different context within a sub-proof may be switched via next, which is just a single block-close followed by block-open again. The effect of next is to reset the local proof context; there is no goal focus involved here! 

For slightly more advanced applications, there are explicit block parentheses as well. These typically achieve a stronger forward style of reasoning. 

next switches to a fresh block within a sub-proof, resetting the local context to the initial one. 

$\{$ { and $\}$ explicitly open and close blocks. Any current facts pass through “{” unchanged, while “}” causes any result to be exported into the enclosing context. Thus fixed variables are generalized, assumptions discharged, and local definitions unfolded (cf. §6.2.1). There is no difference of assume and presume in this mode of forward reasoning — in contrast to plain backward reasoning with the result exported at show time. 

# 6.1.3 Omitting proofs

oops : proof → local_theory | theory 

The oops command discontinues the current proof attempt, while considering the partial proof text as properly processed. This is conceptually quite different from “faking” actual proofs via sorry (see §6.4.2): oops does not observe the proof structure at all, but goes back right to the theory level. Furthermore, oops does not produce any result theorem — there is no intended claim to be able to complete the proof in any way. 

A typical application of oops is to explain Isar proofs within the system itself, in conjunction with the document preparation tools of Isabelle described in chapter 4. Thus partial or even wrong proof attempts can be discussed in a logically sound manner. Note that the Isabelle LATEX macros can be easily adapted to print something like “. . . ” instead of the keyword “oops”. 

# 6.2 Statements

# 6.2.1 Context elements

fix : $p r o o f ( s t a t e ) \to p r o o f ( s t a t e )$ 

assume : $p r o o f ( s t a t e ) \to p r o o f ( s t a t e )$ 

presume : $p r o o f ( s t a t e ) \to p r o o f ( s t a t e )$ 

define : $p r o o f ( s t a t e ) \to p r o o f ( s t a t e )$ 

The logical proof context consists of fixed variables and assumptions. The former closely correspond to Skolem constants, or meta-level universal quantification as provided by the Isabelle/Pure logical framework. Introducing some arbitrary, but fixed variable via “fix $x$ ” results in a local value that may be used in the subsequent proof as any other variable or constant. Furthermore, any result $\vdash \varphi [ x ]$ exported from the context will be universally closed wrt. $x$ at the outermost level: ` Vx. ϕ[x] (this is expressed in normal form using Isabelle’s meta-variables). 

Similarly, introducing some assumption $\chi$ has two effects. On the one hand, a local theorem is created that may be used as a fact in subsequent proof steps. On the other hand, any result $\chi \vdash \varphi$ exported from the context becomes conditional wrt. the assumption: $\vdash \chi \Longrightarrow \varphi$ . Thus, solving an enclosing goal using such a result would basically introduce a new subgoal stemming from the assumption. How this situation is handled depends on the version of assumption command used: while assume insists on solving the subgoal 

by unification with some premise of the goal, presume leaves the subgoal unchanged in order to be proved later by the user. 

Local definitions, introduced by “define $x$ where $x = t ^ { \ast }$ , are achieved by combining “fix x” with another version of assumption that causes any hypothetical equation $x \equiv t$ to be eliminated by the reflexivity rule. Thus, exporting some result $x \equiv t \vdash \varphi [ x ]$ yields $\vdash \varphi [ t ]$ . 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/719757ffb0663a154d306dc1a747290dae28393c469f6bbd0e6d199cbcd3dbbf.jpg)


concl 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/dc236caac9994a6a14f869a9832cb4996b05392b031388102f4fa6abdb312581.jpg)


prems 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4cfe1288c108ed47e14fc7750528486a998425c55da8b8d30c07fc51a2d2ad3d.jpg)


fix $x$ introduces a local variable $x$ that is arbitrary, but fixed. 

assume $a$ : $\varphi$ and presume a: $\varphi$ introduce a local fact $\varphi \vdash \varphi$ by assumption. 

Subsequent results applied to an enclosing goal (e.g. by show) are handled as follows: assume expects to be able to unify with existing premises in the goal, while presume leaves $\varphi$ as new subgoals. 

Several lists of assumptions may be given (separated by and; the resulting list of current facts consists of all of these concatenated. 

A structured assumption like assume $B$ $x$ if $A$ $x$ for $x$ is equivalent to assume $\Lambda x$ . A $x \Longrightarrow B x$ , but vacuous quantification is avoided: a forcontext only effects propositions according to actual use of variables. 

define $x$ where $x = t$ introduces a local (non-polymorphic) definition. In results that are exported from the context, $x$ is replaced by $t$ . 

Internally, equational assumptions are added to the context in Pure form, using $x \equiv t$ instead of $x = t$ or $x \longleftrightarrow t$ from the object-logic. When exporting results from the context, $x$ is generalized and the assumption discharged by reflexivity, causing the replacement by $t$ . 

The default name for the definitional fact is x_def. Several simultaneous definitions may be given as well, with a collective default name. 

It is also possible to abstract over local parameters as follows: define $f : : { \mathit { ' a } } \Rightarrow \mathit { ' b }$ where $f x = t$ for $x : : \mathit { ' a }$ . 

# 6.2.2 Term abbreviations

let : $p r o o f ( s t a t e ) \to p r o o f ( s t a t e )$ 

is : syntax 

Abbreviations may be either bound by explicit let $p \equiv t$ statements, or by annotating assumptions or goal statements with a list of patterns “(is $p _ { 1 } \ldots$ $p _ { n }$ )”. In both cases, higher-order matching is invoked to bind extra-logical term variables, which may be either named schematic variables of the form ? $\ell x$ , or nameless dummies “_” (underscore). Note that in the let form the patterns occur on the left-hand side, while the is patterns are in postfix position. 

Polymorphism of term bindings is handled in Hindley-Milner style, similar to ML. Type variables referring to local assumptions or open goal statements are fixed, while those of finished results or bound by let may occur in arbitrary instances later. Even though actual polymorphism should be rarely used in practice, this mechanism is essential to achieve proper incremental typeinference, as the user proceeds to build up the Isar proof text from left to right. 

Term abbreviations are quite different from local definitions as introduced via define (see §6.2.1). The latter are visible within the logic as actual equations, while abbreviations disappear during the input process just after type checking. Also note that define does not support polymorphism. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/25a0a79546765b56a5ca21adc31241e82580e302668f3d34c80ae974030d2bd2.jpg)


The syntax of is patterns follows term_pat or prop_pat (see §3.3.8). 

let $p _ { 1 } = t _ { 1 }$ and . . . $p _ { n } = t _ { n }$ binds any text variables in patterns $p _ { 1 } , \ldots ,$ $p _ { n }$ by simultaneous higher-order matching against terms $t _ { 1 }$ , . . . , $t _ { n }$ . 

(is $p _ { 1 } \ldots p _ { n }$ ) resembles let, but matches $p _ { 1 }$ , . . . , $p _ { n }$ against the preceding statement. Also note that is is not a separate command, but part of others (such as assume, have etc.). 

Some implicit term abbreviations for goals and facts are available as well. For any open goal, thesis refers to its object-level statement, abstracted over any meta-level parameters (if present). Likewise, this is bound for fact statements resulting from assumptions or finished goals. In case this refers to an objectlogic statement that is an application $f t$ , then $t$ is bound to the special text variable “. . . ” (three dots). The canonical application of this convenience are calculational proofs (see §6.3). 

# 6.2.3 Facts and forward chaining

note : proof(state) $\rightarrow$ proof(state)  
then : proof(state) $\rightarrow$ proof(chain)  
from : proof(state) $\rightarrow$ proof(chain)  
with : proof(state) $\rightarrow$ proof(chain)  
using : proof(prove) $\rightarrow$ proof(prove)  
unfolding : proof(prove) $\rightarrow$ proof(prove)  
use : method  
method_facts : fact 

New facts are established either by assumption or proof of local statements. Any fact will usually be involved in further proofs, either as explicit arguments of proof methods, or when forward chaining towards the next goal via then (and variants); from and with are composite forms involving note. The using elements augments the collection of used facts after a goal has been stated. Note that the special theorem name this refers to the most recently established facts, but only before issuing a follow-up claim. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7e2c888478e9721c8aca1884cfa396bc20f14cf15068901e494b569150d8ce5a.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4fa39ffbde8d7dfd57e201498174adf93aeb220ca14c3e7c2ce1a5d55c446f7d.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e9f003132914044087d1b23c65e2de4930575345a30b64317115e61783ec31c5.jpg)


note a = b1 . . . $b _ { n }$ recalls existing facts $b _ { 1 }$ , . . . , $b _ { n }$ , binding the result as $a$ . Note that attributes may be involved as well, both on the left and right hand sides. 

then indicates forward chaining by the current facts in order to establish the goal to be claimed next. The initial proof method invoked to refine that will be offered the facts to do “anything appropriate” (see also §6.4.2). For example, method rule (see §6.4.3) would typically do an elimination rather than an introduction. Automatic methods usually insert the facts into the goal state before operation. This provides a simple scheme to control relevance of facts in automated proof search. 

from $b$ abbreviates “note $b$ then”; thus then is equivalent to “from this”. 

with $b _ { 1 }$ . . . $b _ { n }$ abbreviates “from $b _ { 1 }$ . . . $b _ { n }$ and this”; thus the forward chaining is from earlier facts together with the current ones. 

using $b _ { 1 }$ . . . $b _ { n }$ augments the facts to be used by a subsequent refinement step (such as apply or proof ). 

unfolding $b _ { 1 }$ . . . $b _ { n }$ is structurally similar to using, but unfolds definitional equations $b _ { 1 }$ . . . $b _ { n }$ throughout the goal state and facts. See also the proof method unfold. 

(use $b _ { 1 }$ . . . $b _ { n }$ in method) uses the facts in the given method expression. The facts provided by the proof state (via using etc.) are ignored, but it is possible to refer to method_facts explicitly. 

method_facts is a dynamic fact that refers to the currently used facts of the goal state. 

Forward chaining with an empty list of theorems is the same as not chaining at all. Thus “from nothing” has no effect apart from entering prove(chain) mode, since nothing is bound to the empty list of theorems. 

Basic proof methods (such as rule) expect multiple facts to be given in their proper order, corresponding to a prefix of the premises of the rule involved. Note that positions may be easily skipped using something like from _ and $a$ and $b$ , for example. This involves the trivial rule PROP $\psi \Longrightarrow P R O P \ \psi$ $\psi$ , which is bound in Isabelle/Pure as “_” (underscore). 

Automated methods (such as simp or auto) just insert any given facts before their usual operation. Depending on the kind of procedure involved, the order of facts is less significant here. 

# 6.2.4 Goals

lemma : local_theory $\rightarrow$ proof(prove)  
theorem : local_theory $\rightarrow$ proof(prove)  
corollary : local_theory $\rightarrow$ proof(prove)  
proposition : local_theory $\rightarrow$ proof(prove)  
schematic_goal : local_theory $\rightarrow$ proof(prove)  
have : proof(state) | proof(chain) $\rightarrow$ proof(prove)  
show : proof(state) | proof(chain) $\rightarrow$ proof(prove)  
hence : proof(state) $\rightarrow$ proof(prove)  
thus : proof(state) $\rightarrow$ proof(prove)  
print_statement* : context $\rightarrow$ 

From a theory context, proof mode is entered by an initial goal command such as lemma. Within a proof context, new claims may be introduced locally; there are variants to interact with the overall proof structure specifically, such as have or show. 

Goals may consist of multiple statements, resulting in a list of facts eventually. A pending multi-goal is internally represented as a meta-level conjunction (&&&), which is usually split into the corresponding number of sub-goals prior to an initial method application, via proof (§6.4.2) or apply (§7.1). The induct method covered in §6.5 acts on multiple claims simultaneously. 

Claims at the theory level may be either in short or long form. A short goal merely consists of several simultaneous propositions (often just one). A long goal includes an explicit context specification for the subsequent conclusion, involving local parameters and assumptions. Here the role of each part of the statement is explicitly marked by separate keywords (see also §5.7); the local assumptions being introduced here are available as assms in the proof. Moreover, there are two kinds of conclusions: shows states several simultaneous propositions (essentially a big conjunction), while obtains claims several simultaneous contexts — essentially a big disjunction of eliminated parameters and assumptions (see §6.6). 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a89a3f421407f403400914e8e9a2dbbd54a7a05452648fc6a325ecefc22ac3a6.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/cd6431484ff94346e65dcb8daa46db593d55175805710a875329fa6fecfc5e44.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/64637dfeec2e0f54337e3ca9a5ffe60384a44d5b9b21710edcbcfd171f9ac826.jpg)


stmt 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0d6cd386f057fc2d8207c4dd8c9fee6e0834103fe1160a14963a8977f54c72e9.jpg)


cond_stmt 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0ca8da8ccc4e6ecfc20e6244419e4963993273f1a1a62c74abec4633c6f3cb3d.jpg)


short_statement 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1252fbd5fe0aa09c1ffc7f319a03da3e1f7a31e3390b55e0f44deac2f5a988a0.jpg)


long_statement 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1a0f580ad4f9b9963ca8730abc462aa7d54a65f660670203188370cd1ee27768.jpg)


context 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b88192b161c08925b4a8fe5c35e07090af642e4660ab1081e2e422249ef02e9a.jpg)


conclusion 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/26e75f512268504f61216af6c3b643fcb70fecb59461c1130ab63794c0b30683.jpg)


obtain_clauses 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/66d35110099601bbd63e2f9c8769473664a022ed8cabe00510d84917e0d8dfda.jpg)


obtain_case 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/bcdd17e53c24c0bf186ce85b3582a9aca97b990a72a56148c21ede1d0a6dcafb.jpg)


lemma $a$ : $\varphi$ enters proof mode with $\varphi$ as main goal, eventually resulting in some fact ` $\varphi$ to be put back into the target context. 

A long_statement may build up an initial proof context for the subsequent claim, potentially including local definitions and syntax; see also includes in §5.3 and context_elem in §5.7. 

A short_statement consists of propositions as conclusion, with an option context of premises and parameters, via if/for in postfix notation, corresponding to assumes/fixes in the long prefix notation. 

Local premises (if present) are called “assms” for long_statement, and “that” for short_statement. 

theorem, corollary, and proposition are the same as lemma. The different command names merely serve as a formal comment in the theory source. 

schematic_goal is similar to theorem, but allows the statement to contain unbound schematic variables. 

Under normal circumstances, an Isar proof text needs to specify claims explicitly. Schematic goals are more like goals in Prolog, where certain results are synthesized in the course of reasoning. With schematic statements, the inherent compositionality of Isar proofs is lost, which also impacts performance, because proof checking is forced into sequential mode. 

have a: $\varphi$ claims a local goal, eventually resulting in a fact within the current logical context. This operation is completely independent of any pending sub-goals of an enclosing goal statements, so have may be freely used for experimental exploration of potential results within a proof body. 

show $a$ : $\varphi$ is like have $a$ : $\varphi$ plus a second stage to refine some pending sub-goal for each one of the finished result, after having been exported 

into the corresponding context (at the head of the sub-proof of this show command). 

To accommodate interactive debugging, resulting rules are printed before being applied internally. Even more, interactive execution of show predicts potential failure and displays the resulting error as a warning beforehand. Watch out for the following message: 

Local statement fails to refine any pending goal 

hence expands to “then have” and thus expands to “then show”. These conflations are left-over from early history of Isar. The expanded syntax is more orthogonal and improves readability and maintainability of proofs. 

print_statement $a$ prints facts from the current theory or proof context in long statement form, according to the syntax for lemma given above. 

Any goal statement causes some term abbreviations (such as ?thesis) to be bound automatically, see also §6.2.2. 

Structured goal statements involving if or when define the special fact that to refer to these assumptions in the proof body. The user may provide separate names according to the syntax of the statement. 

# 6.3 Calculational reasoning

also : proof(state) $\rightarrow$ proof(state) finally : proof(state) $\rightarrow$ proof(chain) moreover : proof(state) $\rightarrow$ proof(state) ultimately : proof(state) $\rightarrow$ proof(chain) print trans rules\* : context $\rightarrow$ trans : attribute sym : attribute symmetric : attribute 

Calculational proof is forward reasoning with implicit application of transitivity rules (such those of =, ≤, <). Isabelle/Isar maintains an auxiliary fact register calculation for accumulating results obtained by transitivity composed with the current result. Command also updates calculation involving this, while finally exhibits the final calculation by forward chaining towards the next goal statement. Both commands require valid current facts, i.e. may 

occur only after commands that produce theorems such as assume, note, or some finished proof of have, show etc. The moreover and ultimately commands are similar to also and finally, but only collect further results in calculation without applying any rules yet. 

Also note that the implicit term abbreviation “. . . ” has its canonical application with calculational proofs. It refers to the argument of the preceding statement. (The argument of a curried infix expression happens to be its right-hand side.) 

Isabelle/Isar calculations are implicitly subject to block structure in the sense that new threads of calculational reasoning are commenced for any new block (as opened by a local goal, for example). This means that, apart from being able to nest calculations, there is no separate begin-calculation command required. 

The Isar calculation proof commands may be defined as follows:1 

also0 ≡ note calculation = this 

$\mathbf { a l s o } _ { n + 1 }$ ≡ note calculation = trans [OF calculation this] 

finally ≡ also from calculation 

moreover ≡ note calculation = calculation this 

ultimately ≡ moreover from calculation 

also 

finally 

add 

del 

trans 

also (a1 . . . an) maintains the auxiliary calculation register as follows. The first occurrence of also in some calculational thread initializes calculation by this. Any subsequent also on the same level of blockstructure updates calculation by some transitivity rule applied to 

calculation and this (in that order). Transitivity rules are picked from the current context, unless alternative rules are given as explicit arguments. 

finally $( a _ { 1 } \ldots a _ { n } )$ maintains calculation in the same way as also and then concludes the current calculational thread. The final result is exhibited as fact for forward chaining towards the next goal. Basically, finally abbreviates also from calculation. Typical idioms for concluding calculational proofs are “finally show ?thesis .” and “finally have $\varphi$ .”. 

moreover and ultimately are analogous to also and finally, but collect results only, without applying rules. 

print_trans_rules prints the list of transitivity rules (for calculational commands also and finally) and symmetry rules (for the symmetric operation and single step elimination patters) of the current context. 

trans declares theorems as transitivity rules. 

sym declares symmetry rules, as well as Pure.elim? rules. 

symmetric resolves a theorem with some rule declared as sym in the current context. For example, “assume [symmetric]: $x = y ^ { , }$ produces a swapped fact derived from that assumption. 

In structured proof texts it is often more appropriate to use an explicit single-step elimination proof, such as “assume $x = y$ then have $y =$ $x$ ..”. 

# 6.4 Refinement steps

# 6.4.1 Proof method expressions

Proof methods are either basic ones, or expressions composed of methods via “,” (sequential composition), “;” (structural composition), “|” (alternative choices), “?” (try), “+” (repeat at least once), “[n]” (restriction to first $n$ subgoals). In practice, proof methods are usually just a comma separated list of name args specifications. Note that parentheses may be dropped for single method specifications (with no arguments). The syntactic precedence of method combinators is | ; , [] + ? (from low to high). 

method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/de94a876cfeb43cf2adb4a6466cc9a81246daac8bb3126d90af9cb2dd5726ca1.jpg)


methods 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/8723ca3e777b5af563eebd302915edcbfadb0c80ea68cf1473979dd085b05f3d.jpg)


Regular Isar proof methods do not admit direct goal addressing, but refer to the first subgoal or to all subgoals uniformly. Nonetheless, the subsequent mechanisms allow to imitate the effect of subgoal addressing that is known from ML tactics. 

Goal restriction means the proof state is wrapped-up in a way that certain subgoals are exposed, and other subgoals are “parked” elsewhere. Thus a proof method has no other chance than to operate on the subgoals that are presently exposed. 

Structural composition “ $m _ { 1 }$ ; $m _ { 2 } { } ^ { , ; }$ means that method $m _ { 1 }$ is applied with restriction to the first subgoal, then $m _ { 2 }$ is applied consecutively with restriction to each subgoal that has newly emerged due to $m _ { 1 }$ . This is analogous to the tactic combinator THEN_ALL_NEW in Isabelle/ML, see also [55]. For example, (rule r; blast) applies rule $r$ and then solves all new subgoals by blast. 

Moreover, the explicit goal restriction operator “ $\lfloor n \rfloor$ ” exposes only the first $n$ subgoals (which need to exist), with default $n = 1$ . For example, the method expression “simp_all[3]” simplifies the first three subgoals, while “(rule $r$ , 

simp_all)[]” simplifies all new goals that emerge from applying rule $r$ to the originally first one. 

Improper methods, notably tactic emulations, offer low-level goal addressing as explicit argument to the individual tactic being involved. Here “[!]” refers to all goals, and “ $\lfloor n - \rfloor$ ” to all goals starting from $n$ . 

goal_spec 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/125307814e631090583912d1c9f7ef6b59e8b59278999c0c19d8eebdbc8c9c88.jpg)


# 6.4.2 Initial and terminal proof steps

proof: proof(prove) $\rightarrow$ proof(state)  
qed: proof(state) $\rightarrow$ proof(state) | local_theory | theory  
by: proof(prove) $\rightarrow$ proof(state) | local_theory | theory  
..: proof(prove) $\rightarrow$ proof(state) | local_theory | theory  
. : proof(prove) $\rightarrow$ proof(state) | local_theory | theory  
sorry: proof(prove) $\rightarrow$ proof(state) | local_theory | theory  
standard: method 

Arbitrary goal refinement via tactics is considered harmful. Structured proof composition in Isar admits proof methods to be invoked in two places only. 

1. An initial refinement step proof $m _ { 1 }$ reduces a newly stated goal to a number of sub-goals that are to be solved later. Facts are passed to $m _ { 1 }$ for forward chaining, if so indicated by proof (chain) mode. 

2. A terminal conclusion step qed $m _ { 2 }$ is intended to solve remaining goals. No facts are passed to $m _ { 2 }$ . 

The only other (proper) way to affect pending goals in a proof body is by show, which involves an explicit statement of what is to be solved eventually. 

Thus we avoid the fundamental problem of unstructured tactic scripts that consist of numerous consecutive goal transformations, with invisible effects. 

As a general rule of thumb for good proof style, initial proof methods should either solve the goal completely, or constitute some well-understood reduction to new sub-goals. Arbitrary automatic proof tools that are prone leave a large number of badly structured sub-goals are no help in continuing the proof document in an intelligible manner. 

Unless given explicitly by the user, the default initial method is standard, which subsumes at least rule or its classical variant rule. These methods apply a single standard elimination or introduction rule according to the topmost logical connective involved. There is no separate default terminal method. Any remaining goals are always solved by assumption in the very last step. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/65598e9f7485a9386804b29ed63217a0bff4dbb4686397bd1617985a03615cf6.jpg)


proof $m _ { 1 }$ refines the goal by proof method $m _ { 1 }$ ; facts for forward chaining are passed if so indicated by proof (chain) mode. 

qed $m _ { 2 }$ refines any remaining goals by proof method $m _ { 2 }$ and concludes the sub-proof by assumption. If the goal had been show, some pending 

sub-goal is solved as well by the rule resulting from the result exported into the enclosing goal context. Thus qed may fail for two reasons: either $m _ { 2 }$ fails, or the resulting rule does not fit to any pending goal2 of the enclosing context. Debugging such a situation might involve temporarily changing show into have, or weakening the local context by replacing occurrences of assume by presume. 

by $m _ { 1 }$ $m _ { 2 }$ is a terminal proof ; it abbreviates proof $m _ { 1 }$ qed $m _ { 2 }$ , but with backtracking across both methods. Debugging an unsuccessful by $m _ { 1 }$ $m _ { 2 }$ command can be done by expanding its definition; in many cases proof $m _ { 1 }$ (or even apply $m _ { 1 }$ ) is already sufficient to see the problem. 

“..” is a standard proof ; it abbreviates by standard. 

“.” is a trivial proof ; it abbreviates by this. 

sorry is a fake proof pretending to solve the pending claim without further ado. This only works in interactive development, or if the quick_and_dirty is enabled. Facts emerging from fake proofs are not the real thing. Internally, the derivation object is tainted by an oracle invocation, which may be inspected via the command thm_oracles (§5.14). 

The most important application of sorry is to support experimentation and top-down proof development. 

standard refers to the default refinement step of some Isar language elements (notably proof and “..”). It is dynamically scoped, so the behaviour depends on the application environment. 

In Isabelle/Pure, standard performs elementary introduction / elimination steps (rule), introduction of type classes (intro_classes) and locales (intro_locales). 

In Isabelle/HOL, standard also takes classical rules into account (cf. §9.4). 

# 6.4.3 Fundamental methods and attributes

The following proof methods and attributes refer to basic logical operations of Isar. Further methods and attributes are provided by several generic and object-logic specific tools and packages (see chapter 9 and part III). 

print_rules∗ : context → 

− : method 

goal_cases : method 

subproofs : method 

fact : method 

assumption : method 

this : method 

rule : method 

intro : attribute 

elim : attribute 

dest : attribute 

rule : attribute 

OF : attribute 

of : attribute 

where : attribute 

goal_cases 

name 

subproofs method 

fact 

thms 

rule 

rulemod 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1a1188faa2efa10a44cf781482a769f2b381b5a2b113ab785ea1e7a7b2f12585.jpg)


print_rules prints rules declared via attributes intro, elim, dest of Isabelle/Pure. 

See also the analogous print_claset command for similar rule declarations of the classical reasoner (§9.4). 

“−” (minus) inserts the forward chaining facts as premises into the goal, and nothing else. 

Note that command proof without any method actually performs a single reduction step using the rule method; thus a plain do-nothing proof step would be “proof $-$ ” rather than proof alone. 

goal_cases $a _ { 1 }$ . . . $a _ { n }$ turns the current subgoals into cases within the context (see also §6.5). The specified case names are used if present; otherwise cases are numbered starting from 1. 

Invoking cases in the subsequent proof body via the case command will fix goal parameters, assume goal premises, and let variable ?case refer to the conclusion. 

subproofs m applies the method expression $m$ consecutively to each subgoal, constructing individual subproofs internally (analogous to “show goal by $m$ ” for each subgoal of the proof state). Search alternatives of $m$ are truncated: the method is forced to be deterministic. This method combinator impacts the internal construction of proof terms: it makes a cascade of let-expressions within the derivation tree and may thus improve scalability. 

fact $a _ { 1 }$ . . . $a _ { n }$ composes some fact from $a _ { 1 }$ , . . . , $a _ { n }$ (or implicitly from the current proof context) modulo unification of schematic type and term variables. The rule structure is not taken into account, i.e. meta-level implication is considered atomic. This is the same principle underlying literal facts (cf. §3.3.9): “have $\varphi$ by fact” is equivalent to “note $^ { c } \varphi ^ { c \prime }$ provided that $\vdash \varphi$ is an instance of some known $\vdash \varphi$ in the proof context. 

assumption solves some goal by a single assumption step. All given facts are guaranteed to participate in the refinement; this means there may be only 0 or 1 in the first place. Recall that qed (§6.4.2) already concludes any remaining sub-goals by assumption, so structured proofs usually need not quote the assumption method at all. 

this applies all of the current facts directly as rules. Recall that “.” (dot) abbreviates “by this”. 

rule $a _ { 1 }$ . . . $a _ { n }$ applies some rule given as argument in backward manner; facts are used to reduce the rule before applying it to the goal. Thus rule without facts is plain introduction, while with facts it becomes elimination. 

When no arguments are given, the rule method tries to pick appropriate rules automatically, as declared in the current context using the intro, elim, dest attributes (see below). This is included in the standard behaviour of proof and “..” (double-dot) steps (see §6.4.2). 

intro, elim, and dest declare introduction, elimination, and destruct rules, to be used with method rule, and similar tools. Note that the latter will ignore rules declared with “?”, while “!” are used most aggressively. 

The classical reasoner (see §9.4) introduces its own variants of these attributes; use qualified names to access the present versions of Isabelle/Pure, i.e. Pure.intro. 

rule del undeclares introduction, elimination, or destruct rules. 

OF $a _ { 1 }$ . . . $a _ { n }$ applies some theorem to all of the given rules $a _ { 1 }$ , . . . , $a _ { n }$ in canonical right-to-left order, which means that premises stemming from the $a _ { i }$ emerge in parallel in the result, without interfering with each other. In many practical situations, the $a _ { i }$ do not have premises themselves, so rule $\left[ O F \ a _ { 1 } \ . . . \ a _ { n } \right]$ can be actually read as functional application (modulo unification). 

Argument positions may be effectively skipped by using “_” (underscore), which refers to the propositional identity rule in the Pure theory. 

of $t _ { 1 }$ . . . $t _ { n }$ performs positional instantiation of term variables. The terms $t _ { 1 }$ , . . . , $t _ { n }$ are substituted for any schematic variables occurring in a theorem from left to right; “_” (underscore) indicates to skip a position. Arguments following a “concl:” specification refer to positions of the conclusion of a rule. 

An optional context of local variables for $x _ { 1 }$ $x _ { 1 } \ldots x .$ $x _ { m }$ may be specified: the instantiated theorem is exported, and these variables become schematic (usually with some shifting of indices). 

where $x _ { 1 } = t _ { 1 }$ and . . . $x _ { n } = t _ { n }$ performs named instantiation of schematic type and term variables occurring in a theorem. Schematic variables have to be specified on the left-hand side (e.g. ?x1.3). The question mark may be omitted if the variable name is a plain identifier without index. As type instantiations are inferred from term instantiations, explicit type instantiations are seldom necessary. 

An optional context of local variables for $x _ { 1 }$ . . . $x _ { m }$ may be specified as for of above. 

# 6.4.4 Defining proof methods

method_setup : local_theory → local_theory 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/bd4c283929b431035902a339141c569f64865673feb6f9a94240088429e6b7e9.jpg)


method_setup name = text description defines a proof method in the current context. The given text has to be an ML expression of type (Proof.context -> Proof.method) context_parser, cf. basic parsers defined in structure Args and Attrib. There are also combinators like METHOD and SIMPLE_METHOD to turn certain tactic forms into official proof methods; the primed versions refer to tactics with explicit goal addressing. 

Here are some example method definitions: 

```txt
method_setup my_method1 = <Scan.succeed (K (SIMPLE_METHOD)' (fn i: int => no_tac)))> "my first method (without any arguments)" 
```

```txt
method_setup my_method2 = <Scan.succeed (fn ctxt: Proof.context => SIMPLE_METHOD' (fn i: int => no_tac))>"my second method (with context)" 
```

```txt
method_setup my_method3 = <Attrib.thms >> (fn thms: thm list => fn ctxt: Proof.context => SIMPLE_METHOD' (fn i: int => no_tac))> "my third method (with theorem arguments and context)" 
```

# 6.5 Proof by cases and induction

# 6.5.1 Rule contexts

case : proof(state) $\rightarrow$ proof(state)
print_cases* : context $\rightarrow$ case_names : attribute
case_conclusion : attribute
params : attribute
consumes : attribute 

The puristic way to build up Isar proof contexts is by explicit language elements like fix, assume, let (see §6.2.1). This is adequate for plain natural 

deduction, but easily becomes unwieldy in concrete verification tasks, which typically involve big induction rules with several cases. 

The case command provides a shorthand to refer to a local context symbolically: certain proof methods provide an environment of named “cases” of the form $c$ : $x _ { 1 }$ , . . . , $x _ { m }$ , $\varphi _ { 1 }$ , . . . , $\varphi _ { n }$ ; the effect of “case $c ^ { \mathfrak { r } }$ is then equivalent to “fix $x _ { 1 }$ . . . $x _ { m }$ assume c: $\varphi _ { 1 }$ . . . $\varphi _ { n }$ ”. Term bindings may be covered as well, notably ?case for the main conclusion. 

By default, the “terminology” $x _ { 1 }$ , . . . , $x _ { m }$ of a case value is marked as hidden, i.e. there is no way to refer to such parameters in the subsequent proof text. After all, original rule parameters stem from somewhere outside of the current proof text. By using the explicit form “case $( c y _ { 1 } \ldots y _ { m } ) ^ { \rangle \rangle }$ instead, the proof author is able to chose local names that fit nicely into the current context. 

It is important to note that proper use of case does not provide means to peek at the current goal state, which is not directly observable in Isar! Nonetheless, goal refinement commands do provide named cases $g o a l _ { i }$ for each subgoal $i$ $= ~ 1$ , . . . , $\boldsymbol { n }$ of the resulting goal state. Using this extra feature requires great care, because some bits of the internal tactical machinery intrude the proof text. In particular, parameter names stemming from the left-over of automated reasoning tools are usually quite unpredictable. 

Under normal circumstances, the text of cases emerge from standard elimination or induction rules, which in turn are derived from previous theory specifications in a canonical way (say from inductive definitions). 

Proper cases are only available if both the proof method and the rules involved support this. By using appropriate attributes, case names, conclusions, and parameters may be also declared by hand. Thus variant versions of rules that have been derived manually become ready to use in advanced case analysis later. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/89a563fe36d0144527e41977e30b621666b46054f4bf587daead3fb78a1c715b.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0d8104777844459f3643925a2bdcfd6ae5d4eddbfb855e73187753360f8b7fc9.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/aa3693b4e358c82bb86db77559b0796fb46e4c30ffb0f70e8cc55672c2b9cd7f.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/3944d2088c2a0bdc7d24387d2febc14bedb5ded7ce044167664790011f9d1dfd.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d2c5d12f3f4539819ad1a76ca52501ee0fc2b30993c82150aea140dc7a1b2f3f.jpg)


case $a$ : $( c x _ { 1 } \ldots x _ { m } )$ invokes a named local context $c$ : $x _ { 1 }$ , . . . , $x _ { m }$ , $\varphi _ { 1 } , \ldots ,$ $\varphi _ { m }$ , as provided by an appropriate proof method (such as cases and induct). The command “case a: $( c \ x _ { 1 } \ . . . \ x _ { m } ) ^ { \prime }$ abbreviates “fix $x _ { 1 } \ldots x _ { }$ $x _ { 1 }$ $x _ { m }$ assume a.c: $\varphi _ { 1 }$ . . . $\varphi _ { n }$ ”. Each local fact is qualified by the prefix $a$ , and all such facts are collectively bound to the name $a$ . 

The fact name is specification $a$ is optional, the default is to re-use $c$ So case $( c x _ { 1 } \ldots x _ { m } )$ is the same as case $c$ : $( c x _ { 1 } \ldots x _ { m } )$ . 

print_cases prints all local contexts of the current state, using Isar proof language notation. 

case_names $c _ { 1 }$ . . . $c _ { k }$ declares names for the local contexts of premises of a theorem; $c _ { 1 }$ , . . . , $c _ { k }$ refers to the prefix of the list of premises. Each of the cases $c _ { i }$ can be of the form $c [ h _ { 1 } \ . . . \ h _ { n } ]$ where the $h _ { 1 }$ . . . $h _ { n }$ are the names of the hypotheses in case $c _ { i }$ from left to right. 

case_conclusion c $d _ { 1 }$ . . . $d _ { k }$ declares names for the conclusions of a named premise $c$ ; here $d _ { 1 }$ , . . . , $d _ { k }$ refers to the prefix of arguments of a logical formula built by nesting a binary connective (e.g. ∨). 

Note that proof methods such as induct and coinduct already provide a default name for the conclusion as a whole. The need to name subformulas only arises with cases that split into several sub-cases, as in common co-induction rules. 

params p1 . . . $p _ { m }$ and . . . q1 . . . $q _ { n }$ renames the innermost parameters of premises 1, . . . , $\boldsymbol { n }$ of some theorem. An empty list of names may be given to skip positions, leaving the present parameters unchanged. 

Note that the default usage of case rules does not directly expose parameters to the proof context. 

consumes n declares the number of “major premises” of a rule, i.e. the number of facts to be consumed when it is applied by an appropriate proof method. The default value of consumes is $n = 1$ , which is appropriate for the usual kind of cases and induction rules for inductive sets (cf. §11.1). Rules without any consumes declaration given are treated as if consumes 0 had been specified. 

A negative $n$ is interpreted relatively to the total number of premises of the rule in the target context. Thus its absolute value specifies the remaining number of premises, after subtracting the prefix of major premises as indicated above. This form of declaration has the technical advantage of being stable under more morphisms, notably those that export the result from a nested context with additional assumptions. 

Note that explicit consumes declarations are only rarely needed; this is already taken care of automatically by the higher-level cases, induct, and coinduct declarations. 

# 6.5.2 Proof methods

cases : method 

induct : method 

induction : method 

coinduct : method 

The cases, induct, induction, and coinduct methods provide a uniform interface to common proof techniques over datatypes, inductive predicates (or 

sets), recursive functions etc. The corresponding rules may be specified and instantiated in a casual manner. Furthermore, these methods provide named local contexts that may be invoked via the case proof command within the subsequent proof text. This accommodates compact proof texts even when reasoning about large specifications. 

The induct method also provides some infrastructure to work with structured statements (either using explicit meta-level connectives, or including facts and parameters separately). This avoids cumbersome encoding of “strengthened” inductive statements within the object-logic. 

Method induction differs from induct only in the names of the facts in the local context invoked by the case command. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fb0ed1e960155ca9313c50a2f4958f59b4bc1defe4b4dded2712815cfc75c557.jpg)


rule 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2c9ee0c843174f255167525fd515712e388135e3c32a70377343246d3915bc41.jpg)


definst 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/250bc9a0fe5706207c13ff6614d4a0e0ec753f0bb176ad79afac0d7404c5da28.jpg)


definsts 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fc153485733679b2c667eb261c6158e63e0ad845c430d1317d2b2d8f5f49e2c7.jpg)


arbitrary 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d6433e0aa70a2ff7bac2379675af30551bc1e752522b857aaa1bd485e66f7028.jpg)


taking 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4c2bd2402fa1a4ec9463583de9c6debe293f23cf482f04a9219d9ed1dcc1e437.jpg)


cases insts $R$ applies method rule with an appropriate case distinction theorem, instantiated to the subjects insts. Symbolic case names are bound according to the rule’s local contexts. 

The rule is determined as follows, according to the facts and arguments passed to the cases method: 

<table><tr><td>facts</td><td></td><td>arguments</td><td>rule</td></tr><tr><td rowspan="3">╞ R</td><td>cases</td><td></td><td>implicit rule R</td></tr><tr><td>cases</td><td></td><td>classical case split</td></tr><tr><td>cases</td><td>t</td><td>datatype exhaustion (type of t)</td></tr><tr><td>╞ A t</td><td>cases</td><td>...</td><td>inductive predicate/set elimination (of A)</td></tr><tr><td>...</td><td>cases</td><td>... rule: R</td><td>explicit rule R</td></tr></table>

Several instantiations may be given, referring to the suffix of premises of the case rule; within each premise, the prefix of variables is instantiated. In most situations, only a single term needs to be specified; this refers to the first variable of the last premise (it is usually the same for all cases). The (no_simp) option can be used to disable pre-simplification of cases (see the description of induct below for details). 

induct insts $R$ and induction insts $R$ are analogous to the cases method, but refer to induction rules, which are determined as follows: 

<table><tr><td>facts</td><td></td><td>arguments</td><td>rule</td></tr><tr><td></td><td>induct</td><td>Px</td><td>datatype induction (type of x)</td></tr><tr><td>⊢ Ax</td><td>induct</td><td>...</td><td>predicate/set induction (of A)</td></tr><tr><td>...</td><td>induct</td><td>... rule: R</td><td>explicit rule R</td></tr></table>

Several instantiations may be given, each referring to some part of a mutual inductive definition or datatype — only related partial induction rules may be used together, though. Any of the lists of terms $P$ , $x$ , . . . refers to the suffix of variables present in the induction rule. This enables the writer to specify only induction variables, or both predicates and variables, for example. 

Instantiations may be definitional: equations $x \equiv t$ introduce local definitions, which are inserted into the claim and discharged after applying the induction rule. Equalities reappear in the inductive cases, but have been transformed according to the induction principle being involved here. In order to achieve practically useful induction hypotheses, some variables occurring in $t$ need to generalized (see below). Instantiations of the form $t$ , where $t$ is not a variable, are taken as a shorthand for $x \equiv t$ , where $x$ is a fresh variable. If this is not intended, $t$ has to be enclosed in parentheses. By default, the equalities generated by definitional instantiations are pre-simplified using a specific set of rules, 

usually consisting of distinctness and injectivity theorems for datatypes. This pre-simplification may cause some of the parameters of an inductive case to disappear, or may even completely delete some of the inductive cases, if one of the equalities occurring in their premises can be simplified to False. The (no_simp) option can be used to disable pre-simplification. Additional rules to be used in pre-simplification can be declared using the induct_simp attribute. 

The optional “arbitrary: $x _ { 1 }$ . . . $x _ { m } ^ { \quad \mathrm { ~ } \mathrm { ~ } ^ { \mathrm { ~ } } }$ specification generalizes variables $x _ { 1 }$ , . . . , $x _ { m }$ of the original goal before applying induction. It is possible to separate variables by “and” to generalize in goals other than the first. Thus induction hypotheses may become sufficiently general to get the proof through. Together with definitional instantiations, one may effectively perform induction over expressions of a certain structure. 

The optional “taking: $t _ { 1 }$ . . . $t _ { n } ^ { \phantom { \dagger } }$ specification provides additional instantiations of a prefix of pending variables in the rule. Such schematic induction rules rarely occur in practice, though. 

coinduct inst $R$ is analogous to the induct method, but refers to coinduction rules, which are determined as follows: 

<table><tr><td>goal</td><td></td><td>arguments</td><td>rule</td></tr><tr><td></td><td>coinduct</td><td>x</td><td>type coinduction (type of x)</td></tr><tr><td>A x</td><td>coinduct</td><td>...</td><td>predicate/set coinduction (of A)</td></tr><tr><td>...</td><td>coinduct</td><td>... rule: R</td><td>explicit rule R</td></tr></table>

Coinduction is the dual of induction. Induction essentially eliminates $A$ $x$ towards a generic result $P$ x, while coinduction introduces $A$ $x$ starting with $B$ $x$ , for a suitable “bisimulation” $B$ . The cases of a coinduct rule are typically named after the predicates or sets being covered, while the conclusions consist of several alternatives being named after the individual destructor patterns. 

The given instantiation refers to the suffix of variables occurring in the rule’s major premise, or conclusion if unavailable. An additional “taking: $t _ { 1 }$ . . . $t _ { n } ^ { \phantom { \dagger } }$ specification may be required in order to specify the bisimulation to be used in the coinduction step. 

Above methods produce named local contexts, as determined by the instantiated rule as given in the text. Beyond that, the induct and coinduct methods guess further instantiations from the goal specification itself. Any persisting unresolved schematic variables of the resulting rule will render the the corresponding case invalid. The term binding ?case for the conclusion will be provided with each case, provided that term is fully specified. 

The print_cases command prints all named cases present in the current proof state. 

Despite the additional infrastructure, both cases and coinduct merely apply a certain rule, after instantiation, while conforming due to the usual way of monotonic natural deduction: the context of a structured statement $\Lambda x _ { 1 } \ldots$ $x _ { m }$ . ϕ1 =⇒ . . . $\varphi _ { n } \implies . . . .$ reappears unchanged after the case split. 

The induct method is fundamentally different in this respect: the meta-level structure is passed through the “recursive” course involved in the induction. Thus the original statement is basically replaced by separate copies, corresponding to the induction hypotheses and conclusion; the original goal context is no longer available. Thus local assumptions, fixed parameters and definitions effectively participate in the inductive rephrasing of the original statement. 

In induct proofs, local assumptions introduced by cases are split into two different kinds: hyps stemming from the rule and prems from the goal statement. This is reflected in the extracted cases accordingly, so invoking “case $c ^ { \mathfrak { I } }$ will provide separate facts c.hyps and c.prems, as well as fact $c$ to hold the allinclusive list. 

In induction proofs, local assumptions introduced by cases are split into three different kinds: IH, the induction hypotheses, hyps, the remaining hypotheses stemming from the rule, and prems, the assumptions from the goal statement. The names are c.IH, c.hyps and c.prems, as above. 

Facts presented to either method are consumed according to the number of “major premises” of the rule involved, which is usually 0 for plain cases and induction rules of datatypes etc. and 1 for rules of inductive predicates or sets and the like. The remaining facts are inserted into the goal verbatim before the actual cases, induct, or coinduct rule is applied. 

# 6.5.3 Declaring rules

print_induct_rules∗ : context → 

cases : attribute 

induct : attribute 

coinduct : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9489347eae69357ea76b67065bae75f378a6eb82b9120284d52057b8ef8deb38.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/db2c15c61d90df821eed77f676e73c3b2b0a0da58bf091c5862f90ffd710fab7.jpg)


spec 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/342c4307b5eb9e4d0baeea1011865b8e6c5522bc3057a7e44c7b10c94bbed29b.jpg)


print_induct_rules prints cases and induct rules for predicates (or sets) and types of the current context. 

cases, induct, and coinduct (as attributes) declare rules for reasoning about (co)inductive predicates (or sets) and types, using the corresponding methods of the same name. Certain definitional packages of objectlogics usually declare emerging cases and induction rules as expected, so users rarely need to intervene. 

Rules may be deleted via the del specification, which covers all of the type/pred/set sub-categories simultaneously. For example, cases del removes any cases rules declared for some type, predicate, or set. 

Manual rule declarations usually refer to the case_names and params attributes to adjust names of cases and parameters of a rule; the consumes declaration is taken care of automatically: consumes 0 is specified for “type” rules and consumes 1 for “predicate” / “set” rules. 

# 6.6 Generalized elimination and case splitting

consider : proof (state) | proof (chain) → proof (prove) 

obtain : proof (state) | proof (chain) → proof (prove) 

Generalized elimination means that hypothetical parameters and premises may be introduced in the current context, potentially with a split into cases. This works by virtue of a locally proven rule that establishes the soundness of this temporary context extension. As representative examples, one may think of standard rules from Isabelle/HOL like this: 

$B \ x \implies ( \bigwedge x . \ B \ x \implies t h e s i s ) \implies t h e s i s$ 

$A \implies B \implies t h e s i s ) \implies$ 

In general, these particular rules and connectives need to get involved at all: this concept works directly in Isabelle/Pure via Isar commands defined below. In particular, the logic of elimination and case splitting is delegated to an Isar proof, which often involves automated tools. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/71b8c97b0f5dba96a2c47ee32661addf7a35eb535d37b6a1394f67159d4280e7.jpg)


concl 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5f603c11097a7245f4838950c3766ba4a07b806a45ec8bbe6bfd7bf50b49ab14.jpg)


prems 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1ed05f018b297d5e0d95b6c8cc004d7b188f129139818544acc061b1ac2f07df.jpg)


consider (a) x where ${ \overline { { A } } } { \mathrm { ~ } } { \overline { { x } } } { \mathrm { ~ } } | { \mathrm { ~ } } ( b )$ y where ${ \overline { { B } } } { \overline { { y } } } \ | \ \ldots$ states a rule for case splitting into separate subgoals, such that each case involves new parameters and premises. After the proof is finished, the resulting rule may be used directly with the cases proof method (§6.5), in order to perform actual case-splitting of the proof text via case and next as usual. 

Optional names in round parentheses refer to case names: in the proof of the rule this is a fact name, in the resulting rule it is used as annotation with the case_names attribute. 

Formally, the command consider is defined as derived Isar language element as follows: 

consider (a) x where ${ \overline { { A } } } { \mathrm { ~ } } { \overline { { x } } } { \mathrm { ~ } } | { \mathrm { ~ } } ( b ) { \mathrm { ~ } } { \overline { { y } } }$ where ${ \overline { { B } } } \ { \overline { { y } } } \ | \ \ldots \ \equiv$ 

have [case_names a b . . . ]: thesis if a [Pure.intro?]: Vx. A x =⇒ thesis 

and b [Pure.intro?]: Vy. B y =⇒ thesis 

and . . 

for thesis 

apply (insert a b . . . ) 

See also §6.2.4 for obtains in toplevel goal statements, as well as print_statement to print existing rules in a similar format. 

obtain $x$ where $\overline { { A } } \overline { { x } }$ states a generalized elimination rule with exactly one case. After the proof is finished, it is activated for the subsequent proof text: the context is augmented via fix $x$ assume $\overline { { A } } \ \overline { { x } }$ , with special provisions to export later results by discharging these assumptions again. 

Note that according to the parameter scopes within the elimination rule, results must not refer to hypothetical parameters; otherwise the export will fail! This restriction conforms to the usual manner of existential reasoning in Natural Deduction. 

Formally, the command obtain is defined as derived Isar language element as follows, using an instrumented variant of assume: 

obtain $\overline{x}$ where $a\colon \overline{A}\overline{x}$ $\langle \text{proof} \rangle \equiv$ havethesis if that [Pure/intro?]: $\bigwedge \overline{x}$ . $\overline{A}\overline{x}\Rightarrow$ thesis forthesis apply (insert that) $\langle \mathrm{proof}\rangle$ fix $\overline{x}$ assume\* $a\colon \overline{A}\overline{x}$ 

In the proof of consider and obtain the local premises are always bound to the fact name that, according to structured Isar statements involving if (§6.2.4). 

Facts that are established by obtain cannot be polymorphic: any typevariables occurring here are fixed in the present context. This is a natural consequence of the role of fix and assume in this construct. 

# Proof scripts

Interactive theorem proving is traditionally associated with “proof scripts”, but Isabelle/Isar is centered around structured proof documents instead (see also chapter 6). 

Nonetheless, it is possible to emulate proof scripts by sequential refinements of a proof state in backwards mode, notably with the apply command (see §7.1). 

There are also various proof methods that allow to refer to implicit goal state information that is not accessible to structured Isar proofs (see §7.3). Note that the subgoal (§7.2) command usually eliminates the need for implicit goal state references. 

# 7.1 Commands for step-wise refinement

supply∗ : $p r o o f ( p r o v e )  p r o o f ( p r o v e )$ 

apply∗ : $p r o o f ( p r o v e )  p r o o f ( p r o v e )$ 

apply_end∗ : proof (state) → proof (state) 

done∗ : proof (prove) → proof (state) | local_theory | theory 

defer∗ : proof → proof 

prefer∗ : proof → proof 

back∗ : proof proof 

supply 

thmdef 

and 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7332c0306b61e0c1a870a38f99029b6773753ae276c8fe560196af8bdca20a6b.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ac988e2bae1cddb7895a0e4649336668baec2143870d64973e8501ea6f9ac781.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/81ea9eeda56561ae823dd08ee319afeddef46c06c8532b5fca612c78aeeb21f8.jpg)


supply supports fact definitions during goal refinement: it is similar to note, but it operates in backwards mode and does not have any impact on chained facts. 

apply $m$ applies proof method $m$ in initial position, but unlike proof it retains $^ { \ast } p r o o f ( p r o v e ) ^ { \ast }$ mode. Thus consecutive method applications may be given just as in tactic scripts. 

Facts are passed to $m$ as indicated by the goal’s forward-chain mode, and are consumed afterwards. Thus any further apply command would always work in a purely backward manner. 

apply_end $m$ applies proof method $m$ as if in terminal position. Basically, this simulates a multi-step tactic script for qed, but may be given anywhere within the proof body. 

No facts are passed to $m$ here. Furthermore, the static context is that of the enclosing goal (as for actual qed). Thus the proof method may not refer to any assumptions introduced in the current body, for example. 

done completes a proof script, provided that the current goal state is solved completely. Note that actual structured proof commands (e.g. “.” or sorry) may be used to conclude proof scripts as well. 

defer $n$ and prefer $n$ shuffle the list of pending goals: defer puts off subgoal $\boldsymbol { n }$ to the end of the list ( $n = 1$ by default), while prefer brings sub-goal $\boldsymbol { n }$ to the front. 

back does back-tracking over the result sequence of the latest proof command. Any proof command may return multiple results, and this command explores the possibilities step-by-step. It is mainly useful for 

experimentation and interactive exploration, and should be avoided in finished proofs. 

# 7.2 Explicit subgoal structure

subgoal∗ : proof → proof 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/130a00688d6722cf1e4978c30374ea30e93ffc21d80a33b34d77009b509df2ed.jpg)


prems 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9736de7b531b17d07a3eecdf1a424b03cbeaa97327949a4acf4e42f747d79a27.jpg)


params 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/452776eb583df7cc98b39bc2a8462327c90654792185d7bff5a1e8cf79f5184f.jpg)


subgoal allows to impose some structure on backward refinements, to avoid proof scripts degenerating into long of apply sequences. 

The current goal state, which is essentially a hidden part of the Isar/VM configuration, is turned into a proof context and remaining conclusion. This corresponds to fix / assume / show in structured proofs, but the text of the parameters, premises and conclusion is not given explicitly. 

Goal parameters may be specified separately, in order to allow referring to them in the proof body: “subgoal for x y z” names a prefix, and “subgoal for . . . x y z” names a suffix of goal parameters. The latter uses a literal \<dots> symbol as notation. Parameter positions may be skipped via dummies (underscore). Unspecified names remain internal, and thus inaccessible in the proof text. 

“subgoal premises prems” indicates that goal premises should be turned into assumptions of the context (otherwise the remaining conclusion is a Pure implication). The fact name and attributes are optional; the particular name “prems” is a common convention for the premises of an arbitrary goal context in proof scripts. 

“subgoal result” indicates a fact name for the result of a proven subgoal. Thus it may be re-used in further reasoning, similar to the result of show in structured Isar proofs. 

Here are some abstract examples: 

lemma $\bigwedge x y z$ . $A x \Rightarrow B y \Rightarrow C z$ and $\bigwedge u v$ . $X u \Rightarrow Y v$ subgoal $\langle \text{proof} \rangle$ subgoal $\langle \text{proof} \rangle$ done 

lemma $\bigwedge x y z$ . $A x \Rightarrow B y \Rightarrow C z$ and $\bigwedge u v$ . $X u \Rightarrow Y v$ subgoal for $x y z$ (proof)  
subgoal for $u v$ (proof) done 

lemma $\bigwedge x y z. A x \Rightarrow B y \Rightarrow C z$ and $\bigwedge u v. X u \Rightarrow Y v$ subgoal premises for $x y z$ using $\langle A x \rangle \langle B y \rangle$ $\langle \text{proof} \rangle$ subgoal premises for $u v$ using $\langle X u \rangle$ $\langle \text{proof} \rangle$ done 

lemma $\bigwedge x y z$ . $A x \Rightarrow B y \Rightarrow C z$ and $\bigwedge u v$ . $X u \Rightarrow Y v$ subgoal $r$ premises prems for $x y z$ proof - have $A x$ by (fact prems) moreover have $B y$ by (fact prems) ultimately show ?thesis <proof> qed subgoal premises prems for $u v$ proof - 

have $\wedge x y z$ $A x\Rightarrow B y\Rightarrow C z$ by (fact $r$ ) moreover have $Xu$ by (fact prems) ultimately show ?thesis $\langle \mathsf{proof}\rangle$ qed done   
lemma $\wedge x y z$ . $A x\Rightarrow B y\Rightarrow C z$ subgoal premises prems for...z proof - from prems show $Cz$ (proof) qed done 

# 7.3 Tactics: improper proof methods

The following improper proof methods emulate traditional tactics. These admit direct access to the goal state, which is normally considered harmful! In particular, this may involve both numbered goal addressing (default 1), and dynamic instantiation within the scope of some subgoal. 

Dynamic instantiations refer to universally quantified parameters of a subgoal • (the dynamic context) rather than fixed variables and term abbreviations of a (static) Isar context. 

Tactic emulation methods, unlike their ML counterparts, admit simultaneous instantiation from both dynamic and static contexts. If names occur in both contexts goal parameters hide locally fixed variables. Likewise, schematic variables refer to term abbreviations, if present in the static context. Otherwise the schematic variable is interpreted as a schematic variable and left to be solved by unification with certain parts of the subgoal. 

Note that the tactic emulation proof methods in Isabelle/Isar are consistently named foo_tac. Note also that variable names occurring on left hand sides of instantiations must be preceded by a question mark if they coincide with a keyword or contain dots. This is consistent with the attribute where (see §6.4.3). 

rule_tac∗ : method 

erule_tac∗ : method 

drule_tac∗ : method 

frule_tac∗ : method 

cut_tac∗ : method 

thin_tac∗ : method 

subgoal_tac∗ : method 

rename_tac∗ : method 

rotate_tac∗ : method 

tactic∗ : method 

raw_tactic∗ : method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/f1a18ea66eb7e2d60be9d58f47f7262e40625d6cf24cc5bfa9062d957816c888.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5be4186ca16f4b2c451fce1eb718c4cb4e72a74785dd0b62b4d9e3e36cdfd30f.jpg)


rule_tac etc. do resolution of rules with explicit instantiation. This works the same way as the ML tactics Rule_Insts.res_inst_tac etc. (see [55]). 

Multiple rules may be only given if there is no instantiation; then rule_tac is the same as resolve_tac in ML (see [55]). 

cut_tac inserts facts into the proof state as assumption of a subgoal; instantiations may be given as well. Note that the scope of schematic variables is spread over the main goal statement and rule premises are turned into new subgoals. This is in contrast to the regular method insert which inserts closed rule statements. 

thin_tac $\varphi$ deletes the specified premise from a subgoal. Note that $\varphi$ may contain schematic variables, to abbreviate the intended proposition; the first matching subgoal premise will be deleted. Removing useless premises from a subgoal increases its readability and can make search tactics run faster. 

subgoal_tac $\varphi _ { 1 }$ . . . $\varphi _ { n }$ adds the propositions $\varphi _ { 1 }$ . . . $\varphi _ { n }$ as local premises to a subgoal, and poses the same as new subgoals (in the original context). 

rename_tac $x _ { 1 }$ . . . $x _ { n }$ renames parameters of a goal according to the list $x _ { 1 }$ , . . . , $x _ { n }$ , which refers to the suffix of variables. 

rotate_tac $\boldsymbol { n }$ rotates the premises of a subgoal by $\boldsymbol { n }$ positions: from right to left if $n$ is positive, and from left to right if $n$ is negative; the default value is 1. 

tactic text produces a proof method from any ML text of type tactic. Apart from the usual ML environment and the current proof context, the ML code may refer to the locally bound values facts, which indicates any current facts used for forward-chaining. 

raw_tactic is similar to tactic, but presents the goal state in its raw internal form, where simultaneous subgoals appear as conjunction of the logical framework instead of the usual split into several subgoals. While feature this is useful for debugging of complex method definitions, it should not never appear in production theories. 

# Inner syntax — the term language

The inner syntax of Isabelle provides concrete notation for the main entities of the logical framework, notably $\lambda$ -terms with types and type classes. Applications may either extend existing syntactic categories by additional notation, or define new sub-languages that are linked to the standard term language via some explicit markers. For example FOO foo could embed the syntax corresponding for some user-defined nonterminal foo — within the bounds of the given lexical syntax of Isabelle/Pure. 

The most basic way to specify concrete syntax for logical entities works via mixfix annotations (§8.2), which may be usually given as part of the original declaration or via explicit notation commands later on (§8.3). This already covers many needs of concrete syntax without having to understand the full complexity of inner syntax layers. 

Further details of the syntax engine involves the classical distinction of lexical language versus context-free grammar (see §8.4), and various mechanisms for syntax transformations (see §8.5). 

# 8.1 Printing logical entities

# 8.1.1 Diagnostic commands

$\begin{array}{rl}\mathbf{typ}^{\ast} & :\text{context}\to \\ \mathbf{term}^{\ast} & :\text{context}\to \\ \mathbf{prop}^{\ast} & :\text{context}\to \\ \mathbf{thm}^{\ast} & :\text{context}\to \\ \mathbf{prf}^{\ast} & :\text{context}\to \\ \mathbf{full\_prf}^{\ast} & :\text{context}\to \\ \mathbf{print\_state}^{\ast} & :\text{any}\to \end{array}$ 

These diagnostic commands assist interactive development by printing internal logical entities in a human-readable fashion. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/8f3e119a837b094ce4cb0cce7aa4c09eb4db9b40f0dfe048ad813d944336bf45.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b2ba71b00752571b04eb696b5c60ba9707f7607c3deac61a5225d7665d90ea2c.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/76b2b93b43467e33356aff0db818f6a985fe773529b11ca6aebcdc4cd957fc54.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fb98c4a047ff381d628b56bcb1044ce204db63f6c8a07f216181b1a96665d7a1.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/966e13d2d9cba4ec02c3f3ca1be0b5079830d76f167f3267264bc19954b9c287.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c3b5d1d6cc29c8375104dfcd0ab30c13b01388c063f38067c06483f3b1dbef73.jpg)


modes 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/557b40f0e31620f102f3f58b05e3c4d8277ae622e6ca8f36bc8b5c34f3c08382.jpg)


typ $\tau$ reads and prints a type expression according to the current context. 

typ $\tau : : s$ uses type-inference to determine the most general way to make $\tau$ conform to sort $s$ . For concrete $\tau$ this checks if the type belongs to that 

sort. Dummy type parameters “_” (underscore) are assigned to fresh type variables with most general sorts, according the the principles of type-inference. 

term $t$ and prop $\varphi$ read, type-check and print terms or propositions according to the current theory or proof context; the inferred type of $t$ is output as well. Note that these commands are also useful in inspecting the current environment of term abbreviations. 

thm $a _ { 1 }$ . . . $a _ { n }$ retrieves theorems from the current theory or proof context. Note that any attributes included in the theorem specifications are applied to a temporary context derived from the current theory or proof; the result is discarded, i.e. attributes involved in $a _ { 1 }$ , . . . , $a _ { n }$ do not have any permanent effect. 

prf displays the (compact) proof term of the current proof state (if present), or of the given theorems. Note that this requires an underlying logic image with proof terms enabled, e.g. HOL−Proofs. 

full_prf is like prf , but displays the full proof term, i.e. also displays information omitted in the compact proof term, which is denoted by “_” placeholders there. 

print_state prints the current proof state (if present), including current facts and goals. 

All of the diagnostic commands above admit a list of modes to be specified, which is appended to the current print mode; see also §8.1.3. Thus the output behavior may be modified according particular print mode features. For example, print_state (latex) prints the current proof state with mathematical symbols and special characters represented in LATEX source, according to the Isabelle style [54]. 

Note that antiquotations (cf. §4.2) provide a more systematic way to include formal items into the printed text document. 

# 8.1.2 Details of printed content

```txt
show_markup : attribute show_types : attribute default false show_sorts : attribute default false show_consts : attribute default false show_abbrevs : attribute default true show_brackets : attribute default false names_long : attribute default false names_short : attribute default false names_unique : attribute default true eta_contract : attribute default true goals_limit : attribute default 10 show_main_goal : attribute default false show_hyps : attribute default false showtags : attribute default false show_questionmarks : attribute default true 
```

These configuration options control the detail of information that is displayed for types, terms, theorems, goals etc. See also §9.1. 

show_markup controls direct inlining of markup into the printed representation of formal entities — notably type and sort constraints. This enables Prover IDE users to retrieve that information via tooltips or popups while hovering with the mouse over the output window, for example. Consequently, this option is enabled by default for Isabelle/jEdit. 

show_types and show_sorts control printing of type constraints for term variables, and sort constraints for type variables. By default, neither of these are shown in output. If show_sorts is enabled, types are always shown as well. In Isabelle/jEdit, manual setting of these options is normally not required thanks to show_markup above. 

Note that displaying types and sorts may explain why a polymorphic inference rule fails to resolve with some goal, or why a rewrite rule does not apply as expected. 

show_consts controls printing of types of constants when displaying a goal state. 

Note that the output can be enormous, because polymorphic constants often occur at several different type instances. 

show_abbrevs controls folding of constant abbreviations. 

show_brackets controls bracketing in pretty printed output. If enabled, all sub-expressions of the pretty printing tree will be parenthesized, even if this produces malformed term syntax! This crude way of showing the internal structure of pretty printed entities may occasionally help to diagnose problems with operator priorities, for example. 

names_long, names_short, and names_unique control the way of printing fully qualified internal names in external form. See also §4.2 for the document antiquotation options of the same names. 

eta_contract controls $\eta$ -contracted printing of terms. 

The $\eta$ -contraction law asserts $( \lambda x . \ f x ) \equiv f$ , provided $x$ is not free in $f$ It asserts extensionality of functions: $f \equiv g$ if $\textit { f x } \equiv \textit { g x }$ for all $x$ . Higher-order unification frequently puts terms into a fully $\eta$ -expanded form. For example, if $F$ has type $( \tau \Rightarrow \tau ) \Rightarrow \tau$ then its expanded form is λh. $F$ (λx . h x ). 

Enabling eta_contract makes Isabelle perform $\eta$ -contractions before printing, so that λh. $F$ (λx. h x) appears simply as $F$ . 

Note that the distinction between a term and its $\eta$ -expanded form occasionally matters. While higher-order resolution and rewriting operate modulo $\alpha \beta \eta$ -conversion, some other tools might look at terms more discretely. 

goals_limit controls the maximum number of subgoals to be printed. 

show_main_goal controls whether the main result to be proven should be displayed. This information might be relevant for schematic goals, to inspect the current claim that has been synthesized so far. 

show_hyps controls printing of implicit hypotheses of local facts. Normally, only those hypotheses are displayed that are not covered by the assumptions of the current context: this situation indicates a fault in some tool being used. 

By enabling show_hyps, output of all hypotheses can be enforced, which is occasionally useful for diagnostic purposes. 

show_tags controls printing of extra annotations within theorems, such as internal position information, or the case names being attached by the attribute case_names. 

Note that the tagged and untagged attributes provide low-level access to the collection of tags associated with a theorem. 

show_question_marks controls printing of question marks for schematic variables, such as ? $\ell x$ . Only the leading question mark is affected, the remaining text is unchanged (including proper markup for schematic variables that might be relevant for user interfaces). 

# 8.1.3 Alternative print modes

print_mode_value: unit -> string list 

Print_Mode.with_modes: string list -> (’a -> ’b) -> ’a -> ’b 

The print mode facility allows to modify various operations for printing. Commands like typ, term, thm (see §8.1.1) take additional print modes as optional argument. The underlying ML operations are as follows. 

print_mode_value () yields the list of currently active print mode names. This should be understood as symbolic representation of certain individual features for printing (with precedence from left to right). 

Print_Mode.with_modes modes f x evaluates $f x$ in an execution context where the print mode is prepended by the given modes. This provides a thread-safe way to augment print modes. It is also monotonic in the set of mode names: it retains the default print mode that certain user-interfaces might have installed for their proper functioning! 

The pretty printer for inner syntax maintains alternative mixfix productions for any print mode name invented by the user, say in commands like notation or abbreviation. Mode names can be arbitrary, but the following ones have a specific meaning by convention: 

• "" (the empty string): default mode; implicitly active as last element in the list of modes. 

• input: dummy print mode that is never active; may be used to specify notation that is only available for input. 

• internal dummy print mode that is never active; used internally in Isabelle/Pure. 

• ASCII: prefer ASCII art over mathematical symbols. 

• latex: additional mode that is active in LATEX document preparation of Isabelle theory sources; allows to provide alternative output notation. 

# 8.2 Mixfix annotations

Mixfix annotations specify concrete inner syntax of Isabelle types and terms. Locally fixed parameters in toplevel theorem statements, locale and class specifications also admit mixfix annotations in a fairly uniform manner. A mixfix annotation describes the concrete syntax, the translation to abstract syntax, and the pretty printing. Special case annotations provide a simple means of specifying infix operators and binders. 

Isabelle mixfix syntax is inspired by obj [17]. It allows to specify any contextfree priority grammar, which is more general than the fixity declarations of ML and Prolog. 


mixfix


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/66f6467519150b7170bb4d9e6085c576c717d1f622ddc5adf7812b749810bfd1.jpg)



template


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/224ff5f782201f43ba36e7ed27b2a418f1caa965828ee95dd8c475eb2c817519.jpg)



prios


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/261a0dff876b33fe3a59fb2be404d3d3c43d8ba98396eb131f9dbee13f763bb2.jpg)


prio 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/eab156349c88381067f617bd297be1fe5001860262c153c9282a77986e9fe587.jpg)


The mixfix template may include literal text, spacing, blocks, and arguments (denoted by “_”); the special symbol “\<index>” (printed as “ı”) represents an index argument that specifies an implicit structure reference (see also §5.7). Only locally fixed variables may be declared as structure. 

Infix and binder declarations provide common abbreviations for particular mixfix declarations. So in practice, mixfix templates mostly degenerate to literal text for concrete syntax, such as “++” for an infix symbol. 

# 8.2.1 The general mixfix form

In full generality, mixfix declarations work as follows. Suppose a constant $c$ :: $\tau _ { 1 } \Rightarrow . . .$ . $\tau _ { n } \Rightarrow \tau$ is annotated by $( m i x f i x \ [ p _ { 1 } , \ldots , \ p _ { n } ] \ p )$ , where mixfix is a string $d _ { 0 } \_ d _ { 1 } \_ \dots \_ d _ { n }$ consisting of delimiters that surround argument positions as indicated by underscores. 

Altogether this determines a production for a context-free priority grammar, where for each argument $i$ the syntactic category is determined by $\tau _ { i }$ (with priority $p _ { i }$ ), and the result category is determined from $\tau$ (with priority $p$ ). Priority specifications are optional, with default 0 for arguments and 1000 for the result.1 

Since $\tau$ may be again a function type, the constant type scheme may have more argument positions than the mixfix pattern. Printing a nested application c $t _ { 1 }$ . . . $t _ { m }$ for $m > n$ works by attaching concrete notation only to the innermost part, essentially by printing (c t1 . . . tn) . . . $t _ { m }$ instead. If a term has fewer arguments than specified in the mixfix template, the concrete syntax is ignored. 

A mixfix template may also contain additional directives for pretty printing, notably spaces, blocks, and breaks. The general template format is a sequence over any of the following entities. 

$d$ is a delimiter, namely a non-empty sequence delimiter items of the following form: 

# 1. a control symbol followed by a cartouche

2. a single symbol, excluding the following special characters: 

, single quote 

underscore 

ı index symbol 

( open parenthesis 

) close parenthesis 

/ slash 

‹ › cartouche delimiters 

’ escapes the special meaning of these meta-characters, producing a literal version of the following character, unless that is a blank. 

A single quote followed by a blank separates delimiters, without affecting printing, but input tokens may have additional white space here. 

_ is an argument position, which stands for a certain syntactic category in the underlying grammar. 

ı is an indexed argument position; this is the place where implicit structure arguments can be attached. 

$s$ is a non-empty sequence of spaces for printing. This and the following specifications do not affect parsing at all. 

( $\boldsymbol { n }$ opens a pretty printing block. The optional natural number specifies the block indentation, i.e. how much spaces to add when a line break occurs within the block. The default indentation is 0. 

(‹properties› opens a pretty printing block, with properties specified within the given text cartouche. The syntax and semantics of the category mixfix_properties is described below. 

) closes a pretty printing block. 

// forces a line break. 

/s allows a line break. Here $s$ stands for the string of spaces (zero or more) right after the slash. These spaces are printed if the break is not taken. 

Block properties allow more control over the details of pretty-printed output. The concrete syntax is defined as follows. 

mixfix_properties 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/557daf642326c42c9fe339d809ccc4d6bf02373e9ad6048a27ced13d17bcf8b0.jpg)


entry 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b7497885fd183d026668ca1d2f170c1a5a0c5b7203fa660c4e288a3e8b282169.jpg)


atom 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/54b32109a961676c994ca6326e223f00858baee6054451ae3c4cfc777be35346.jpg)


Each entry is a name-value pair: if the value is omitted, it defaults to true (intended for Boolean properties). The following standard block properties are supported: 

• indent (natural number): the block indentation — the same as for the simple syntax without block properties. 

• consistent (Boolean): this block has consistent breaks (if one break is taken, all breaks are taken). 

• unbreakable (Boolean): all possible breaks of the block are disabled (turned into spaces). 

• markup (string): the optional name of the markup node. If this is provided, all remaining properties are turned into its XML attributes. This allows to specify free-form PIDE markup, e.g. for specialized output. 

Note that the general idea of pretty printing with blocks and breaks is described in [47]; it goes back to [41]. 

# 8.2.2 Infixes

Infix operators are specified by convenient short forms that abbreviate general mixfix annotations as follows: 

$$
\begin{array}{l} \text {(i n f i x} ^ {\prime \prime} s y ^ {\prime \prime} p) \quad \mapsto \quad \left(^ {\prime \prime} (_ {-} s y / _ {-}) ^ {\prime \prime} [ p + 1, p + 1 ] p\right) \\ \text {(i n f i x l} ^ {\prime \prime} s y ^ {\prime \prime} p) \quad \mapsto \quad \left(^ {\prime \prime} (\_ s y / \_)" [ p, p + 1 ] p) \right. \\ \left(\operatorname {i n f i x r} ^ {\prime \prime} s y ^ {\prime \prime} p\right) \mapsto \left(^ {\prime \prime} (\_ s y / \_)" [ p + 1, p ] p\right) \\ \end{array}
$$

The mixfix template $" ( \underline { { \mathbf { \Pi } } } _ { - } \ s y / \ \underline { { \mathbf { \Pi } } } _ { - } ) "$ specifies two argument positions; the delimiter is preceded by a space and followed by a space or line break; the entire phrase is a pretty printing block. 

The alternative notation (sy) is introduced in addition. Thus any infix operator may be written in prefix form (as in Haskell), independently of the number of arguments. 

# 8.2.3 Binders

A binder is a variable-binding construct such as a quantifier. The idea to formalize $\forall x$ . $b$ as All (λx. b) for $A l l : : ( { \mathit { \iota } } ^ { \prime } a \Rightarrow b o o l ) \Rightarrow b o o l$ already goes back to [14]. Isabelle declarations of certain higher-order operators may be annotated with binder annotations as follows: 

$$
c::" \left(\tau_{1}\Rightarrow \tau_{2}\right)\Rightarrow \tau_{3}"\quad (\mathbf{b i n d e r}"s y" [ p ] q)
$$

This introduces concrete binder syntax sy $x$ . $b$ , where $x$ is a bound variable of type $\tau _ { 1 }$ , the body $b$ has type $\tau _ { 2 }$ and the whole term has type $\tau _ { 3 }$ . The optional integer $p$ specifies the syntactic priority of the body; the default is $q$ , which is also the priority of the whole construct. 

Internally, the binder syntax is expanded to something like this: 

$$
c \_ b i n d e r:: " i d t s \Rightarrow \tau_ {2} \Rightarrow \tau_ {3}" \quad (\prime (3 s y _ {-}. / \_)" [ 0, p ] q)
$$

Here idts is the nonterminal symbol for a list of identifiers with optional type constraints (see also §8.4.3). The mixfix template $" ( 3 s y _ { - } . / \mathrm { ~ \underline { ~ } ~ } ) "$ defines argument positions for the bound identifiers and the body, separated by a dot with optional line break; the entire phrase is a pretty printing block of indentation level 3. Note that there is no extra space after $s y$ , so it needs to be included user specification if the binder syntax ends with a token that may be continued by an identifier token at the start of idts. 

Furthermore, a syntax translation to transforms c_binder $x _ { 1 }$ . . . $x _ { n }$ b into iterated application $c$ $( \lambda x _ { 1 } . \ . \ . \ c \ ( \lambda x _ { n } . \ b ) . . . )$ . This works in both directions, for parsing and printing. 

# 8.3 Explicit notation

type_notation : local theoray $\rightarrow$ local_theory   
no_type_notation : local_theory $\rightarrow$ local_theory   
notation : local_theory $\rightarrow$ local_theory   
no_notation : local_theory $\rightarrow$ local_theory   
write : proof(state) $\rightarrow$ proof(state) 

Commands that introduce new logical entities (terms or types) usually allow to provide mixfix annotations on the spot, which is convenient for default notation. Nonetheless, the syntax may be modified later on by declarations for explicit notation. This allows to add or delete mixfix annotations for of existing logical entities within the current context. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/28b0cdea3b1cde42d9ae8d45f221a0ade3bf00c267afebf0ada81d3a2a278dc7.jpg)


type_notation $c$ (mx) associates mixfix syntax with an existing type constructor. The arity of the constructor is retrieved from the context. 

no_type_notation is similar to type_notation, but removes the specified syntax annotation from the present context. 

notation $c$ (mx) associates mixfix syntax with an existing constant or fixed variable. The type declaration of the given entity is retrieved from the context. 

no_notation is similar to notation, but removes the specified syntax annotation from the present context. 

write is similar to notation, but works within an Isar proof body. 

# 8.4 The Pure syntax

# 8.4.1 Lexical matters

The inner lexical syntax vaguely resembles the outer one (§3.2), but some details are different. There are two main categories of inner syntax tokens: 

1. delimiters — the literal tokens occurring in productions of the given priority grammar (cf. §8.4.2); 

2. named tokens — various categories of identifiers etc. 

Delimiters override named tokens and may thus render certain identifiers inaccessible. Sometimes the logical context admits alternative ways to refer to the same entity, potentially via qualified names. 

The categories for named tokens are defined once and for all as follows, reusing some categories of the outer token syntax (§3.2). 

$$
i d = s h o r t \_ i d e n t
$$

$$
l o n g i d = l o n g \_ i d e n t
$$

$$
\begin{array}{r c l} v a r & = & v a r \end{array}
$$

$$
t i d = t y p e \_ i d e n t
$$

$$
t v a r = t y p e \_ v a r
$$

$$
\begin{array}{r c l} \text {n u m \_ t o k e n} & = & \text {n a t} \end{array}
$$

$$
f l o a t \_ t o k e n = n a t. n a t
$$

$$
\text {s t r \_ t o k e n} = ^ {\prime \prime} \dots^ {\prime \prime}
$$

$$
\text {s t r i n g \_ t o k e n} = ^ {\prime \prime} \dots^ {\prime \prime}
$$

$$
c a r t o u c h e = \backslash <   o p e n > \dots \backslash <   c l o s e >
$$

The token categories num_token, float_token, str_token, string_token, and cartouche are not used in Pure. Object-logics may implement numerals and string literals by adding appropriate syntax declarations, together with some translation functions (e.g. see ~~/src/HOL/Tools/string_syntax.ML). 

The derived categories num_const, and float_const, provide robust access to the respective tokens: the syntax tree holds a syntactic constant instead of a free variable. 

Formal document comments (§3.3.5) may be also used within the inner syntax. 

# 8.4.2 Priority grammars

A context-free grammar consists of a set of terminal symbols, a set of nonterminal symbols and a set of productions. Productions have the form $A =$ $\gamma$ , where $A$ is a nonterminal and $\gamma$ is a string of terminals and nonterminals. One designated nonterminal is called the root symbol. The language defined by the grammar consists of all strings of terminals that can be derived from the root symbol by applying productions as rewrite rules. 

The standard Isabelle parser for inner syntax uses a priority grammar. Each nonterminal is decorated by an integer priority: $A ^ { ( p ) }$ . In a derivation, $A ^ { ( p ) }$ may be rewritten using a production $A ^ { ( q ) } = \gamma$ only if $p \leq q$ . Any priority grammar can be translated into a normal context-free grammar by introducing new nonterminals and productions. 

Formally, a set of context free productions $G$ induces a derivation relation $\longrightarrow _ { G }$ as follows. Let $\alpha$ and $\beta$ denote strings of terminal or nonterminal symbols. Then $\alpha ~ A ^ { ( p ) } ~ \beta ~ { \longrightarrow } _ { G } ~ \alpha ~ \gamma ~ \beta$ holds if and only if $G$ contains some production $A ^ { ( q ) } = \gamma$ for $p \leq q$ . 

The following grammar for arithmetic expressions demonstrates how binding power and associativity of operators can be enforced by priorities. 

$$
\begin{array}{l} A ^ {(1 0 0 0)} = (A ^ {(0)}) \\ A ^ {(1 0 0 0)} = 0 \\ A ^ {(0)} = A ^ {(0)} + A ^ {(1)} \\ A ^ {(2)} = A ^ {(3)} * A ^ {(2)} \\ A ^ {(3)} = - A ^ {(3)} \\ \end{array}
$$

The choice of priorities determines that - binds tighter than $^ *$ , which binds tighter than $^ +$ . Furthermore $^ +$ associates to the left and $^ *$ to the right. 

For clarity, grammars obey these conventions: 

• All priorities must lie between 0 and 1000. 

• Priority 0 on the right-hand side and priority 1000 on the left-hand side may be omitted. 

• The production $A ^ { ( p ) } = \alpha$ is written as $A = \alpha$ (p), i.e. the priority of the left-hand side actually appears in a column on the far right. 

• Alternatives are separated by |. 

• Repetition is indicated by dots (. . . ) in an informal but obvious way. 

Using these conventions, the example grammar specification above takes the form: 

$$
\begin{array}{r c l} A & = & (A) \\ | & 0 \\ | & A + A ^ {(1)} & (0) \\ | & A ^ {(3)} * A ^ {(2)} & (2) \\ | & - A ^ {(3)} & (3) \end{array}
$$

# 8.4.3 The Pure grammar

The priority grammar of the Pure theory is defined approximately like this: 

$$
a n y = p r o p \mid l o g i c
$$

$$
\begin{array}{r c l} p r o p & = & (p r o p) \\ & \mid & p r o p ^ {(4)}:: t y p e \\ & \mid & a n y ^ {(3)} = = a n y ^ {(3)} \\ & \mid & a n y ^ {(3)} \equiv a n y ^ {(3)} \\ & \mid & p r o p ^ {(3)} \& \& \& p r o p ^ {(2)} \\ & \mid & p r o p ^ {(2)} = = > p r o p ^ {(1)} \\ & \mid & p r o p ^ {(2)} \Longrightarrow p r o p ^ {(1)} \\ & \mid & [ | p r o p ; \ldots ; p r o p | ] = = > p r o p ^ {(1)} \\ & \mid & [   [ p r o p ; \ldots ; p r o p   ]   ] \Longrightarrow p r o p ^ {(1)} \\ & \mid & !! i d t s. p r o p \\ & \mid & \bigwedge i d t s. p r o p \\ & \mid & O F C L A S S (t y p e, l o g i c) \end{array} \tag {3}
$$

```txt
SORTCONSTRAINT（type） TERM logic PROP aprop 
```

$a_{prop} = (a_{prop})$ $| id | _ { l o n g i d } | _ { v a r } | _ { - } | \dots$ $\begin{array}{l}\mid \mathrm{CONST}id\mid \mathrm{CONST}longid\\ \mid \mathrm{XCONST}id\mid \mathrm{XCONST}longid\\ \mid \mathrm{logic}^{(1000)}\mathrm{any}^{(1000)}\ldots \mathrm{any}^{(1000)} \end{array}$ (999) 

logic $= \mathrm{(logic)}$ | logic(4) :: type (3)  
| id | longid | var | _ | ...  
| CONST id | CONST longid  
| XCONST id | XCONST longid  
| logic(1000) any(1000) ... any(1000) (999)  
| % pptrns . any(3) (3)  
| λ pptrns . any(3) (3)  
| (=) | (≡) | (&&)  
| (=>) | (=Rightarrow)  
| TYPE (type) 

```txt
idt = (idt) | id | _  
| id :: type  
| -: type 
```

index = $\langle \hat{\mathbf{b}}\mathbf{s}\mathbf{u}\mathbf{b} \rangle$ logic(0) $\langle \hat{\mathbf{e}}\mathbf{s}\mathbf{u}\mathbf{b} \rangle$ | | 1 

idts = idt | $idt^{(1)}$ idts (0) 

pttrn $=$ idt 

pttrns $=$ pttrn | pttrn(1) ptttns (0) 

type $=$ (type) |tid|tvar|_ |tid::sort|tvar::sort|_::sort |type_name|type(1000）type_name |（type，...，type）type_name 

$$
\mid \quad t y p e ^ {(1)} \Rightarrow t y p e \tag {0}
$$

$$
\mid \quad t y p e ^ {(1)} \Rightarrow t y p e \tag {0}
$$

$$
[ t y p e, \dots , t y p e ] \Rightarrow t y p e \tag {0}
$$

$$
\mid [ \text {t y p e}, \dots , \text {t y p e} ] \Rightarrow \text {t y p e} \tag {0}
$$

$$
t y p e \_ n a m e = i d | l o n g i d
$$

$$
s o r t = c l a s s \_ n a m e | \_ | \{\}
$$

$$
| \quad \{\text {c l a s s} _ {\text {n a m e}}, \dots , \text {c l a s s} _ {\text {n a m e}} \}
$$

$$
c l a s s \_ n a m e = i d | l o n g i d
$$

Here literal terminals are printed verbatim; see also §8.4.1 for further token categories of the inner syntax. The meaning of the nonterminals defined by the above grammar is as follows: 

any denotes any term. 

prop denotes meta-level propositions, which are terms of type prop. The syntax of such formulae of the meta-logic is carefully distinguished from usual conventions for object-logics. In particular, plain $\lambda$ -term notation is not recognized as prop. 

aprop denotes atomic propositions, which are embedded into regular prop by means of an explicit PROP token. 

Terms of type prop with non-constant head, e.g. a plain variable, are printed in this form. Constants that yield type prop are expected to provide their own concrete syntax; otherwise the printed version will appear like logic and cannot be parsed again as prop. 

logic denotes arbitrary terms of a logical type, excluding type prop. This is the main syntactic category of object-logic entities, covering plain $\lambda$ -term notation (variables, abstraction, application), plus anything defined by the user. 

When specifying notation for logical entities, all logical types (excluding prop) are collapsed to this single category of logic. 

index denotes an optional index term for indexed syntax. If omitted, it refers to the first structure variable in the context. The special dummy “ı” serves as pattern variable in mixfix annotations that introduce indexed notation. 

idt denotes identifiers, possibly constrained by types. 

idts denotes a sequence of idt. This is the most basic category for variables in iterated binders, such as $\lambda$ or $\Lambda$ . 

pttrn and pttrns denote patterns for abstraction, cases bindings etc. In Pure, these categories start as a merely copy of idt and idts, respectively. Object-logics may add additional productions for binding forms. 

type denotes types of the meta-logic. 

sort denotes meta-level sorts. 

Here are some further explanations of certain syntax features. 

• In idts, note that x :: nat $y$ is parsed as $x : : ( n a t \ y )$ , treating $y$ like a type constructor applied to nat. To avoid this interpretation, write ( $x$ :: nat) $y$ with explicit parentheses. 

• Similarly, x :: nat $y : : n a t$ is parsed as $x : ( n a t y : : n a t )$ . The correct form is (x :: nat) $( y : : n a t )$ , or (x :: nat) $y : : \ n a t$ if $y$ is last in the sequence of identifiers. 

• Type constraints for terms bind very weakly. For example, $x < y : : n a t$ is normally parsed as $( x < y ) : : n a t$ , unless $<$ < has a very low priority, in which case the input is likely to be ambiguous. The correct form is $x < ( y : \mathit { n a t } )$ . 

• Dummy variables (written as underscore) may occur in different roles. 

A sort “_” refers to a vacuous constraint for type variables, which is effectively ignored in type-inference. 

A type “_” or “_ :: sort” acts like an anonymous inference parameter, which is filled-in according to the most general type produced by the type-checking phase. 

A bound “_” refers to a vacuous abstraction, where the body does not refer to the binding introduced here. As in the term $\lambda x \_ x$ , which is $\alpha$ -equivalent to λx y. x. 

A free “_” refers to an implicit outer binding. Higher definitional packages usually allow forms like $f x _ { - } = x$ . 

A schematic “_” (within a term pattern, see §3.3.8) refers to an anonymous variable that is implicitly abstracted over its context of locally bound variables. For example, this allows pattern matching of $\{ x . \ f \ x \ = \ g \ x \}$ against $\{ x . \_ \_ = - \}$ , or even $\{ \_ { \cdot - } = - \}$ by using both bound and schematic dummies. 

The three literal dots “...” may be also written as ellipsis symbol \<dots>. In both cases this refers to a special schematic variable, which is bound in the context. This special term abbreviation works nicely with calculational reasoning (§6.3). 

CONST ensures that the given identifier is treated as constant term, and passed through the parse tree in fully internalized form. This is particularly relevant for translation rules (§8.5.2), notably on the RHS. 

XCONST is similar to CONST, but retains the constant name as given. This is only relevant to translation rules (§8.5.2), notably on the LHS. 

# 8.4.4 Inspecting the syntax

print_syntax∗ : context → 

print_syntax prints the inner syntax of the current context. The output can be quite large; the most important sections are explained below. 

lexicon lists the delimiters of the inner token language; see §8.4.1. 

productions lists the productions of the underlying priority grammar; see §8.4.2. 

Many productions have an extra $. . . \implies n a m e$ . These names later become the heads of parse trees; they also guide the pretty printer. 

Productions without such parse tree names are called copy productions. Their right-hand side must have exactly one nonterminal symbol (or named token). The parser does not create a new parse tree node for copy productions, but simply returns the parse tree of the right-hand symbol. 

If the right-hand side of a copy production consists of a single nonterminal without any delimiters, then it is called a chain production. Chain productions act as abbreviations: conceptually, they are removed from the grammar by adding new productions. 

Priority information attached to chain productions is ignored. 

print modes lists the alternative print modes provided by this grammar; see §8.1.3. 

parse_rules and print_rules relate to syntax translations (macros); see §8.5.2. 

parse_ast_translation and print_ast_translation list sets of constants that invoke translation functions for abstract syntax trees, which are only required in very special situations; see §8.5.3. 

parse_translation and print_translation list the sets of constants that invoke regular translation functions; see §8.5.3. 

# 8.4.5 Ambiguity of parsed expressions

syntax_ambiguity_warning : attribute default true 

syntax_ambiguity_limit : attribute default 10 

Depending on the grammar and the given input, parsing may be ambiguous. Isabelle lets the Earley parser enumerate all possible parse trees, and then tries to make the best out of the situation. Terms that cannot be typechecked are filtered out, which often leads to a unique result in the end. Unlike regular type reconstruction, which is applied to the whole collection of input terms simultaneously, the filtering stage only treats each given term in isolation. Filtering is also not attempted for individual types or raw ASTs (as required for translations). 

Certain warning or error messages are printed, depending on the situation and the given configuration options. Parsing ultimately fails, if multiple results remain after the filtering phase. 

syntax_ambiguity_warning controls output of explicit warning messages about syntax ambiguity. 

syntax_ambiguity_limit determines the number of resulting parse trees that are shown as part of the printed message in case of an ambiguity. 

# 8.5 Syntax transformations

The inner syntax engine of Isabelle provides separate mechanisms to transform parse trees either via rewrite systems on first-order ASTs (§8.5.2), or ML functions on ASTs or syntactic $\lambda$ -terms (§8.5.3). This works both for parsing and printing, as outlined in figure 8.1. 

These intermediate syntax tree formats eventually lead to a pre-term with all names and binding scopes resolved, but most type information still missing. Explicit type constraints might be given by the user, or implicit position 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d8316fc23b00a00935c789eb5c36f052d49c661d2cda18292125d09aeb6785af.jpg)



Figure 8.1: Parsing and printing with translations


information by the system — both need to be passed-through carefully by syntax transformations. 

Pre-terms are further processed by the so-called check and uncheck phases that are intertwined with type-inference (see also [55]). The latter allows to operate on higher-order abstract syntax with proper binding and type information already available. 

As a rule of thumb, anything that manipulates bindings of variables or constants needs to be implemented as syntax transformation (see below). Anything else is better done via check/uncheck: a prominent example application is the abbreviation concept of Isabelle/Pure. 

# 8.5.1 Abstract syntax trees

The ML datatype Ast.ast explicitly represents the intermediate AST format that is used for syntax rewriting (§8.5.2). It is defined in ML as follows: 

```txt
datatype ast =  
    Constant of string |  
    Variable of string |  
    Appl of ast list 
```

An AST is either an atom (constant or variable) or a list of (at least two) subtrees. Occasional diagnostic output of ASTs uses notation that resembles 

S-expression of LISP. Constant atoms are shown as quoted strings, variable atoms as non-quoted strings and applications as a parenthesized list of subtrees. For example, the AST 

Ast.Appl [Ast.Constant "_abs", Ast.Variable "x", Ast.Variable "t"] 

is pretty-printed as ("_abs" x t). Note that () and (x) are excluded as ASTs, because they have too few subtrees. 

AST application is merely a pro-forma mechanism to indicate certain syntactic structures. Thus (c a b) could mean either term application or type application, depending on the syntactic context. 

Nested application like (("_abs" x t) u) is also possible, but ASTs are definitely first-order: the syntax constant "_abs" does not bind the ${ \bf x }$ in any way. Proper bindings are introduced in later stages of the term syntax, where ("_abs" x t) becomes an Abs node and occurrences of x in $^ \texttt { t }$ are replaced by bound variables (represented as de-Bruijn indices). 

# AST constants versus variables

Depending on the situation — input syntax, output syntax, translation patterns — the distinction of atomic ASTs as Ast.Constant versus Ast.Variable serves slightly different purposes. 

Input syntax of a term such as f a $b = c$ does not yet indicate the scopes of atomic entities $f$ , a, $b$ , $c$ : they could be global constants or local variables, even bound ones depending on the context of the term. Ast.Variable leaves this choice still open: later syntax layers (or translation functions) may capture such a variable to determine its role specifically, to make it a constant, bound variable, free variable etc. In contrast, syntax translations that introduce already known constants would rather do it via Ast.Constant to prevent accidental re-interpretation later on. 

Output syntax turns term constants into Ast.Constant and variables (free or schematic) into Ast.Variable. This information is precise when printing fully formal $\lambda$ -terms. 

AST translation patterns (§8.5.2) that represent terms cannot distinguish constants and variables syntactically. Explicit indication of CONST c inside the term language is required, unless $c$ is known as special syntax constant (see also syntax). It is also possible to use syntax declarations (without mixfix annotation) to enforce that certain unqualified names are always treated as constant within the syntax machinery. 

The situation is simpler for ASTs that represent types or sorts, since the concrete syntax already distinguishes type variables from type constants (constructors). So $( ^ { \prime } a , ^ { \prime } b )$ foo corresponds to an AST application of some constant for foo and variable arguments for $' a$ and $' b$ . Note that the postfix application is merely a feature of the concrete syntax, while in the AST the constructor occurs in head position. 

# Authentic syntax names

Naming constant entities within ASTs is another delicate issue. Unqualified names are resolved in the name space tables in the last stage of parsing, after all translations have been applied. Since syntax transformations do not know about this later name resolution, there can be surprises in boundary cases. 

Authentic syntax names for Ast.Constant avoid this problem: the fullyqualified constant name with a special prefix for its formal category (class, type, const, fixed) represents the information faithfully within the untyped AST format. Accidental overlap with free or bound variables is excluded as well. Authentic syntax names work implicitly in the following situations: 

• Input of term constants (or fixed variables) that are introduced by concrete syntax via notation: the correspondence of a particular grammar production to some known term entity is preserved. 

• Input of type constants (constructors) and type classes — thanks to explicit syntactic distinction independently on the context. 

• Output of term constants, type constants, type classes — this information is already available from the internal term to be printed. 

In other words, syntax transformations that operate on input terms written as prefix applications are difficult to make robust. Luckily, this case rarely occurs in practice, because syntax forms to be translated usually correspond to some concrete notation. 

# 8.5.2 Raw syntax and translations

nonterminal : theory $\rightarrow$ theory syntax : local_theory $\rightarrow$ local_theory no_syma: local_theory $\rightarrow$ local_theory translations : theory $\rightarrow$ theory no_translations : theory $\rightarrow$ theory syntax_ast_trace : attribute default false syntax_ast.stats : attribute default false 

Unlike mixfix notation for existing formal entities (§8.3), raw syntax declarations provide full access to the priority grammar of the inner syntax, without any sanity checks. This includes additional syntactic categories (via nonterminal) and free-form grammar productions (via syntax). Additional syntax translations (or macros, via translations) are required to turn resulting parse trees into proper representations of formal entities again. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0e8c897195e21448561c59150443429be446fbe6530a2d519345ca15733991b0.jpg)


# constdecl

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e7dae4e25652f691e78142248e217ac9b0a5f987d982c7b471fbe5b7f022484b.jpg)


# mode

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/28c12e53ed522b5f4902108b6cd73ca05580c842911497fcf00507e69da41902.jpg)


# transpat

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4d5ed12b18ed15ad9c586d49ebd8acedfc4ddb2c87b8ef7e4203966234b8a620.jpg)


nonterminal $c$ declares a type constructor $c$ (without arguments) to act as purely syntactic type: a nonterminal symbol of the inner syntax. 

syntax (mode) c :: σ (mx) augments the priority grammar and the pretty printer table for the given print mode (default ""). An optional keyword output means that only the pretty printer table is affected. 

Following §8.2, the mixfix annotation mx = template ps $q$ together with type $\sigma = \tau _ { 1 } \Rightarrow . . .$ $\tau _ { n } \Rightarrow \tau$ and specify a grammar production. The template contains delimiter tokens that surround $n$ argument positions (_). The latter correspond to nonterminal symbols $A _ { i }$ derived from the argument types $\tau _ { i }$ as follows: 

• prop if $\tau _ { i } = p r o p$ 

• logic if $\tau _ { i } = ( \dots ) \kappa$ for logical type constructor $\kappa \neq p r o p$ 

• any if $\tau _ { i } = \alpha$ for type variables 

• $\kappa$ if $\tau _ { i } = \kappa$ for nonterminal $\kappa$ (syntactic type constructor) 

Each $A _ { i }$ is decorated by priority $p _ { i }$ from the given list ps; missing priorities default to 0. 

The resulting nonterminal of the production is determined similarly from type $\tau$ , with priority $q$ and default 1000. 

Parsing via this production produces parse trees $t _ { 1 }$ , . . . , $t _ { n }$ for the argument slots. The resulting parse tree is composed as c $t _ { 1 }$ . . . $t _ { n }$ , by using the syntax constant $c$ of the syntax declaration. 

Such syntactic constants are invented on the spot, without formal check wrt. existing declarations. It is conventional to use plain identifiers prefixed by a single underscore (e.g. _foobar). Names should be chosen with care, to avoid clashes with other syntax declarations. 

The special case of copy production is specified by $c = "$ (empty string). It means that the resulting parse tree $t$ is copied directly, without any further decoration. 

no_syntax (mode) decls removes grammar declarations (and translations) resulting from decls, which are interpreted in the same manner as for syntax above. 

translations rules specifies syntactic translation rules (i.e. macros) as firstorder rewrite rules on ASTs (§8.5.1). The theory context maintains two independent lists translation rules: parse rules $= >$ or ) and print rules (<= or )). For convenience, both can be specified simultaneously as parse / print rules (== or 
). 

Translation patterns may be prefixed by the syntactic category to be used for parsing; the default is logic which means that regular term syntax is used. Both sides of the syntax translation rule undergo parsing and parse AST translations §8.5.3, in order to perform some fundamental normalization like λx y. $b \sim \lambda x$ . λy. $b$ , but other AST translation rules are not applied recursively here. 

When processing AST patterns, the inner syntax lexer runs in a different mode that allows identifiers to start with underscore. This accommodates the usual naming convention for auxiliary syntax constants — those that do not have a logical counter part — by allowing to specify arbitrary AST applications within the term syntax, independently of the corresponding concrete syntax. 

Atomic ASTs are distinguished as Ast.Constant versus Ast.Variable as follows: a qualified name or syntax constant declared via syntax, or parse tree head of concrete notation becomes Ast.Constant, anything else Ast.Variable. Note that CONST and XCONST within the term language (§8.4.3) allow to enforce treatment as constants. 

AST rewrite rules (lhs, rhs) need to obey the following side-conditions: 

• Rules must be left linear: lhs must not contain repeated variables.2 

• Every variable in rhs must also occur in lhs. 

no_translations rules removes syntactic translation rules, which are interpreted in the same manner as for translations above. 

syntax_ast_trace and syntax_ast_stats control diagnostic output in the AST normalization process, when translation rules are applied to concrete input or output. 

Raw syntax and translations provides a slightly more low-level access to the grammar and the form of resulting parse trees. It is often possible to avoid this untyped macro mechanism, and use type-safe abbreviation or notation instead. Some important situations where syntax and translations are really need are as follows: 

• Iterated replacement via recursive translations. For example, consider list enumeration $[ a , b , c , d ]$ as defined in theory HOL.List. 

• Change of binding status of variables: anything beyond the built-in binder mixfix annotation requires explicit syntax translations. For example, consider the set comprehension syntax $\{ x . \ P \}$ as defined in theory HOL.Set. 

# Applying translation rules

As a term is being parsed or printed, an AST is generated as an intermediate form according to figure 8.1. The AST is normalized by applying translation rules in the manner of a first-order term rewriting system. We first examine how a single rule is applied. 

Let $t$ be the abstract syntax tree to be normalized and (lhs, rhs) some translation rule. A subtree $u$ of $t$ is called redex if it is an instance of lhs; in this case the pattern lhs is said to match the object u. A redex matched by lhs may be replaced by the corresponding instance of rhs, thus rewriting the AST $t$ . Matching requires some notion of place-holders in rule patterns: Ast.Variable serves this purpose. 

More precisely, the matching of the object $u$ against the pattern lhs is performed as follows: 

• Objects of the form Ast.Variable $x$ or Ast.Constant $x$ are matched by pattern Ast.Constant $x$ . Thus all atomic ASTs in the object are treated as (potential) constants, and a successful match makes them actual constants even before name space resolution (see also §8.5.1). 

• Object $u$ is matched by pattern Ast.Variable $x$ , binding $x$ to $u$ 

• Object Ast.Appl us is matched by Ast.Appl ts if us and ts have the same length and each corresponding subtree matches. 

• In every other case, matching fails. 

A successful match yields a substitution that is applied to rhs, generating the instance that replaces $u$ . 

Normalizing an AST involves repeatedly applying translation rules until none are applicable. This works yoyo-like: top-down, bottom-up, top-down, etc. At each subtree position, rules are chosen in order of appearance in the theory definitions. 

The configuration options syntax_ast_trace and syntax_ast_stats might help to understand this process and diagnose problems. 

If syntax translation rules work incorrectly, the output of print_syntax with • its rules sections reveals the actual internal forms of AST pattern, without potentially confusing concrete syntax. Recall that AST constants appear as quoted strings and variables without quotes. 

If eta_contract is set to true, terms will be $\eta$ -contracted before the AST rewriter : sees them. Thus some abstraction nodes needed for print rules to match may vanish. For example, Ball A (λx. P x) would contract to Ball A $P$ and the standard print rule would fail to apply. This problem can be avoided by hand-written ML translation functions (see also §8.5.3), which is in fact the same mechanism used in built-in binder declarations. 

# 8.5.3 Syntax translation functions

parse__ast__(translation : theory $\rightarrow$ theory  
parse__translation : theory $\rightarrow$ theory  
print__(translation : theory $\rightarrow$ theory  
typed__(translation : theory $\rightarrow$ theory  
print__(translation : theory $\rightarrow$ theory  
class__(syntax : ML antiquotation  
type__(syntax : ML antiquotation  
const__(syntax : ML antiquotation  
syntax__(const : ML antiquotation 

Syntax translation functions written in ML admit almost arbitrary manipulations of inner syntax, at the expense of some complexity and obscurity in the implementation. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a54712bab8d06b4416dacaa11a026746bc33879f70613c4035f7018d87d9079c.jpg)


parse_translation etc. declare syntax translation functions to the theory. Any of these commands have a single text argument that refers to an ML expression of appropriate type as follows: 

```ocaml
parse_ast translators : (string \* (Proof.context -> Ast. ast list -> Ast. ast)) list   
parseTranslator : (string \* (Proof.context -> term list -> term)) list   
printTranslator : (string \* (Proof.context -> term list -> term)) list   
typed_printTranslator : (string \* (Proof.context -> typ -> term list -> term)) list   
printAstTranslator : (string \* (Proof.context -> Ast. ast list -> Ast. ast)) list 
```

The argument list consists of $( c , \ t r )$ pairs, where $c$ is the syntax name of the formal entity involved, and tr a function that translates a syntax form c args into tr ctxt args (depending on the context). The Isabelle/ML naming convention for parse translations is $c \_ t r$ and for print translations $c \_ t r ^ { \prime }$ . 

The print_syntax command displays the sets of names associated with the translation functions of a theory under parse_ast_translation etc. 

$\mathbb { O } \{ c l a s s \_ s y n t a x \ c \}$ , $\mathbb { O } \{ { t y p e \_ s y n t a x \ c } \}$ , $\mathbb { O } \{ c o n s t \_ s y n t a x \ c \}$ inline the authentic syntax name of the given formal entities into the ML source. This is the fully-qualified logical name prefixed by a special marker to indicate its kind: thus different logical name spaces are properly distinguished within parse trees. 

$\mathbb { Q } \{ c o n s t \_ s y n t a x \ c \}$ inlines the name $c$ of the given syntax constant, having checked that it has been declared via some syntax commands within the theory context. Note that the usual naming convention makes syntax constants start with underscore, to reduce the chance of accidental clashes with other names occurring in parse trees (unqualified constants etc.). 

# The translation strategy

The different kinds of translation functions are invoked during the transformations between parse trees, ASTs and syntactic terms (cf. figure 8.1). Whenever a combination of the form c x1 . . . $x _ { n }$ is encountered, and a translation function $f$ of appropriate kind is declared for $c$ , the result is produced by evaluation of $f$ $\mathbf { \dot { \psi } } \left[ x _ { 1 } , \dots , x _ { n } \right]$ in ML. 

For AST translations, the arguments $x _ { 1 }$ , . . . , $x _ { n }$ are ASTs. A combination has the form Ast.Constant $c$ or Ast.Appl [Ast.Constant c, x1, . . . , $x _ { n } ]$ . 

For term translations, the arguments are terms and a combination has the form Const $( c , \tau )$ or Const (c, τ ) $ x1 $ . . . $ $x _ { n }$ . Terms allow more sophisticated transformations than ASTs do, typically involving abstractions and bound variables. Typed print translations may even peek at the type $\tau$ of the constant they are invoked on, although some information might have been suppressed for term output already. 

Regardless of whether they act on ASTs or terms, translation functions called during the parsing process differ from those for printing in their overall behaviour: 

Parse translations are applied bottom-up. The arguments are already in translated form. The translations must not fail; exceptions trigger an error message. There may be at most one function associated with any syntactic name. 

Print translations are applied top-down. They are supplied with arguments that are partly still in internal form. The result again undergoes translation; therefore a print translation should not introduce as head the very constant that invoked it. The function may raise exception Match to indicate failure; in this event it has no effect. Multiple functions associated with some syntactic name are tried in the order of declaration in the theory. 

Only constant atoms — constructor Ast.Constant for ASTs and Const for terms — can invoke translation functions. This means that parse translations can only be associated with parse tree heads of concrete syntax, or syntactic constants introduced via other translations. For plain identifiers within the term language, the status of constant versus variable is not yet know during parsing. This is in contrast to print translations, where constants are explicitly known from the given term in its fully internal form. 

# 8.5.4 Built-in syntax transformations

Here are some further details of the main syntax transformation phases of figure 8.1. 

# Transforming parse trees to ASTs

The parse tree is the raw output of the parser. It is transformed into an AST according to some basic scheme that may be augmented by AST translation functions as explained in §8.5.3. 

The parse tree is constructed by nesting the right-hand sides of the productions used to recognize the input. Such parse trees are simply lists of tokens and constituent parse trees, the latter representing the nonterminals of the productions. Ignoring AST translation functions, parse trees are transformed to ASTs by stripping out delimiters and copy productions, while retaining some source position information from input tokens. 

The Pure syntax provides predefined AST translations to make the basic $\lambda$ -term structure more apparent within the (first-order) AST representation, and thus facilitate the use of translations (see also §8.5.2). This covers ordinary term application, type application, nested abstraction, iterated meta implications and function types. The effect is illustrated on some representative input strings is as follows: 

<table><tr><td>input source</td><td>AST</td></tr><tr><td>f x y z</td><td>(f x y z)</td></tr><tr><td>&#x27;a ty</td><td>(ty &#x27;a)</td></tr><tr><td>(&#x27;a, &#x27;b)ty</td><td>(ty &#x27;a &#x27;b)</td></tr><tr><td>λx y z. t</td><td>(&quot;abs&quot; x (&quot;_abs&quot; y (&quot;_abs&quot; z t)))</td></tr><tr><td>λx :: &#x27;a. t</td><td>(&quot;abs&quot; (&quot;_constrain&quot; x &#x27;a) t)</td></tr><tr><td>[[P; Q; R]] ⇒ S</td><td>(&quot;Pure.IMP&quot; P (&quot;Pure.IMP&quot; Q (&quot;Pure.IMP&quot; R S))</td></tr><tr><td>[&#x27;a, &#x27;b, &#x27;c] ⇒ &#x27;d</td><td>(&quot;fun&quot; &#x27;a (&quot;fun&quot; &#x27;b (&quot;fun&quot; &#x27;c &#x27;d)))</td></tr></table>

Note that type and sort constraints may occur in further places — translations need to be ready to cope with them. The built-in syntax transformation from parse trees to ASTs insert additional constraints that represent source positions. 

# Transforming ASTs to terms

After application of macros (§8.5.2), the AST is transformed into a term. This term still lacks proper type information, but it might contain some constraints consisting of applications with head _constrain, where the second argument is a type encoded as a pre-term within the syntax. Type inference later introduces correct types, or indicates type errors in the input. 

Ignoring parse translations, ASTs are transformed to terms by mapping AST constants to term constants, AST variables to term variables or constants (according to the name space), and AST applications to iterated term applications. 

The outcome is still a first-order term. Proper abstractions and bound variables are introduced by parse translations associated with certain syntax 

constants. Thus ("_abs" x x) eventually becomes a de-Bruijn term Abs ("x", _, Bound 0). 

# Printing of terms

The output phase is essentially the inverse of the input phase. Terms are translated via abstract syntax trees into pretty-printed text. 

Ignoring print translations, the transformation maps term constants, variables and applications to the corresponding constructs on ASTs. Abstractions are mapped to applications of the special constant _abs as seen before. Type constraints are represented via special _constrain forms, according to various policies of type annotation determined elsewhere. Sort constraints of type variables are handled in a similar fashion. 

After application of macros (§8.5.2), the AST is finally pretty-printed. The built-in print AST translations reverse the corresponding parse AST translations. 

For the actual printing process, the priority grammar (§8.4.2) plays a vital role: productions are used as templates for pretty printing, with argument slots stemming from nonterminals, and syntactic sugar stemming from literal tokens. 

Each AST application with constant head $c$ and arguments $t _ { 1 }$ , . . . , $t _ { n }$ (for $n = 0$ the AST is just the constant $c$ itself) is printed according to the first grammar production of result name $c$ . The required syntax priority of the argument slot is given by its nonterminal $A ^ { ( p ) }$ . The argument $t _ { i }$ that corresponds to the position of $A ^ { ( p ) }$ is printed recursively, and then put in parentheses $i f$ its priority $p$ requires this. The resulting output is concatenated with the syntactic sugar according to the grammar production. 

If an AST application $( c \ x _ { 1 } \ \dots \ x _ { m } )$ has more arguments than the corresponding production, it is first split into ((c x1 . . . xn) $x _ { n + 1 } \ldots x _ { m }$ ) and then printed recursively as above. 

Applications with too few arguments or with non-constant head or without a corresponding production are printed in prefix-form like $f t _ { 1 }$ . . . $t _ { n }$ for terms. Multiple productions associated with some name $c$ are tried in order of appearance within the grammar. An occurrence of some AST variable $x$ is printed as $x$ outright. 

White space is not inserted automatically. If blanks (or breaks) are required to separate tokens, they need to be specified in the mixfix declaration (§8.2). 

# Generic tools and packages

# 9.1 Configuration options

Isabelle/Pure maintains a record of named configuration options within the theory or proof context, with values of type bool, int, real, or string. Tools may declare options in ML, and then refer to these values (relative to the context). Thus global reference variables are easily avoided. The user may change the value of a configuration option by means of an associated attribute of the same name. This form of context declaration works particularly well with commands such as declare or using like this: 

declare $[ [ s h o w \_ m a i n \_ g o a l = f a l s e ] ]$ 

notepad 

begin 

note $[ [ s h o w \_ m a i n \_ g o a l = t r u e ] ]$ 

end 

print_options : context → 

print_options 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e44a28e691dd1fa87140e3a916f1c568faaf15b312be19704cb7d489b29036f3.jpg)


print_options prints the available configuration options, with names, types, and current values; the “!” option indicates extra verbosity. 

$n a m e = v a l u e$ as an attribute expression modifies the named option, with the syntax of the value depending on the option’s type. For bool the default value is true. Any attempt to change a global option in a local context is ignored. 

# 9.2 Basic proof tools

# 9.2.1 Miscellaneous methods and attributes

unfold : method 

fold : method 

insert : method 

erule∗ : method 

drule∗ : method 

frule∗ : method 

intro : method 

elim : method 

fail : method 

succeed : method 

sleep : method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7530c1825aac21acfdf335689afe4afe4036efb6d013fc90cac23c638332b03d.jpg)


unfold $a _ { 1 }$ . . . $a _ { n }$ and fold $a _ { 1 }$ . . . $a _ { n }$ expand (or fold back) the given definitions throughout all goals; any chained facts provided are inserted into the goal and subject to rewriting as well. 

Unfolding works in two stages: first, the given equations are used directly for rewriting; second, the equations are passed through the attribute abs_def before rewriting — to ensure that definitions are fully expanded, regardless of the actual parameters that are provided. 

insert $a _ { 1 }$ . . . $a _ { n }$ inserts theorems as facts into all goals of the proof state. Note that current facts indicated for forward chaining are ignored. 

erule $a _ { 1 }$ . . . $a _ { n }$ , drule $a _ { 1 }$ . . . $a _ { n }$ , and frule $a _ { 1 }$ . . . $a _ { n }$ are similar to the basic rule method (see §6.4.3), but apply rules by elim-resolution, destructresolution, and forward-resolution, respectively [55]. The optional natural number argument (default 0) specifies additional assumption steps to be performed here. 

Note that these methods are improper ones, mainly serving for experimentation and tactic script emulation. Different modes of basic rule application are usually expressed in Isar at the proof language level, rather than via implicit proof state manipulations. For example, 

a proper single-step elimination would be done using the plain rule method, with forward chaining of current facts. 

intro and elim repeatedly refine some goal by intro- or elim-resolution, after having inserted any chained facts. Exactly the rules given as arguments are taken into account; this allows fine-tuned decomposition of a proof problem, in contrast to common automated tools. 

fail yields an empty result sequence; it is the identity of the “|” method combinator (cf. §6.4.1). 

succeed yields a single (unchanged) result; it is the identity of the “,” method combinator (cf. §6.4.1). 

sleep s succeeds after a real-time delay of $s$ seconds. This is occasionally useful for demonstration and testing purposes. 

```txt
tagged : attribute  
untagged : attribute  
THEN : attribute  
unfolded : attribute  
folded : attribute  
abs_def : attribute  
rotated : attribute  
elim_format : attribute  
no_vars* : attribute 
```

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/6cb729c506f2435bd533fc231302cd04f59aa28d626f176a9d21235a7d95fe4c.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/77477a5be0e3efca1143b6261d1d910039b689bdebd248e3afca178321cae2c8.jpg)


tagged name value and untagged name add and remove tags of some theorem. Tags may be any list of string pairs that serve as formal comment. The first string is considered the tag name, the second its value. Note that untagged removes any tags of the same name. 

THEN a composes rules by resolution; it resolves with the first premise of $a$ (an alternative position may be also specified). See also RS in [55]. 

unfolded $a _ { 1 }$ . . . $a _ { n }$ and folded $a _ { 1 }$ . . . $a _ { n }$ expand and fold back again the given definitions throughout a rule. 

abs_def turns an equation of the form $f \ x \ y \equiv t$ into $f \equiv \lambda x y .$ $t$ , which ensures that simp steps always expand it. This also works for objectlogic equality. 

rotated n rotate the premises of a theorem by $n$ (default 1). 

elim_format turns a destruction rule into elimination rule format, by resolving with the rule PROP $A \implies$ ( $P R O P ~ A \Longrightarrow ~ P R O P ~ B ) \Longrightarrow ~ P R O P$ $B$ . 

Note that the Classical Reasoner (§9.4) provides its own version of this operation. 

no_vars replaces schematic variables by free ones; this is mainly for tuning output of pretty printed theorems. 

# 9.2.2 Low-level equational reasoning

subst : method 

hypsubst : method 

split : method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a9f6b9a0fafcc1868d4b9907da7c18a4559d47ad3527c1c67e016ba0e00ccf7a.jpg)


These methods provide low-level facilities for equational reasoning that are intended for specialized applications only. Normally, single step calculations would be performed in a structured text (see also §6.3), while the Simplifier methods provide the canonical way for automated normalization (see §9.3). 

subst eq performs a single substitution step using rule eq, which may be either a meta or object equality. 

subst (asm) eq substitutes in an assumption. 

subst $( i \dots j )$ eq performs several substitutions in the conclusion. The numbers $i$ to $j$ indicate the positions to substitute at. Positions are ordered from the top of the term tree moving down from left to right. For example, in $( a + b ) + ( c + d )$ there are three positions where commutativity of $^ +$ is applicable: 1 refers to $a ~ + ~ b$ , 2 to the whole term, and 3 to $c + d$ . 

If the positions in the list $( i \dots j )$ are non-overlapping (e.g. (2 3) in $( a + b ) + ( c + d ) )$ you may assume all substitutions are performed simultaneously. Otherwise the behaviour of subst is not specified. 

subst (asm) $( \textit { i } \dots \textit { j } )$ eq performs the substitutions in the assumptions. The positions refer to the assumptions in order from left to right. For example, given in a goal of the form $P$ $^ { \circ } \left( a + b \right) \Longrightarrow P \left( c + d \right) \Longrightarrow \ldots ,$ position 1 of commutativity of $^ +$ is the subterm $a + b$ and position 2 is the subterm $c + d$ . 

hypsubst performs substitution using some assumption; this only works for equations of the form $x = t$ where $x$ is a free or bound variable. 

split $a _ { 1 }$ . . . $a _ { n }$ performs single-step case splitting using the given rules. Splitting is performed in the conclusion or some assumption of the subgoal, depending of the structure of the rule. 

Note that the simp method already involves repeated application of split rules as declared in the current context, using split, for example. 

# 9.3 The Simplifier

The Simplifier performs conditional and unconditional rewriting and uses contextual information: rule declarations in the background theory or local proof context are taken into account, as well as chained facts and subgoal premises (“local assumptions”). There are several general hooks that allow to modify the simplification strategy, or incorporate other proof tools that solve sub-problems, produce rewrite rules on demand etc. 

The rewriting strategy is always strictly bottom up, except for congruence rules, which are applied while descending into a term. Conditions in conditional rewrite rules are solved recursively before the rewrite rule is applied. 

The default Simplifier setup of major object logics (HOL, HOLCF, FOL, ZF) makes the Simplifier ready for immediate use, without engaging into the internal structures. Thus it serves as general-purpose proof tool with the main focus on equational reasoning, and a bit more than that. 

# 9.3.1 Simplification methods

```txt
simp : method  
simp_all : method  
Pure.simp : method  
Pure.simp_all : method  
simp_depth_limit : attribute default 100 
```

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/33d0a706c15b7db58c94b066095e22fb1f4cb251af21d4ed19cd005470378551.jpg)


opt 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c2c689ac2ac7100460351d1e4b55a6cc47de0f2bb85e6432db3ede128f4b0bc5.jpg)


simpmod 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/483fe6a8c92aac12ef5944fb6a069d4bbe050d315b98c6c57754cc4edacea0e5.jpg)


simp invokes the Simplifier on the first subgoal, after inserting chained facts as additional goal premises; further rule declarations may be included via (simp add: facts). The proof method fails if the subgoal remains unchanged after simplification. 

Note that the original goal premises and chained facts are subject to simplification themselves, while declarations via add/del merely follow the policies of the object-logic to extract rewrite rules from theorems, without further simplification. This may lead to slightly different behavior in either case, which might be required precisely like that in some boundary situations to perform the intended simplification step! 

Modifier flip deletes the following theorems from the simpset and adds their symmetric version (i.e. lhs and rhs exchanged). No warning is shown if the original theorem was not present. 

The only modifier first removes all other rewrite rules, looper tactics (including split rules), congruence rules, and then behaves like add. Implicit solvers remain, which means that trivial rules like reflexivity or introduction of True are available to solve the simplified subgoals, but also non-trivial tools like linear arithmetic in HOL. The latter may lead to some surprise of the meaning of “only” in Isabelle/HOL compared to English! 

The split modifiers add or delete rules for the Splitter (see also §9.3.6 on the looper). This works only if the Simplifier method has been properly setup to include the Splitter (all major object logics such HOL, HOLCF, FOL, ZF do this already). The ! option causes the split rules to be used aggressively: after each application of a split rule in the conclusion, the safe tactic of the classical reasoner (see §9.4.5) is applied to the new goal. The net effect is that the goal is split into the different cases. This option can speed up simplification of goals with many nested conditional or case expressions significantly. 

There is also a separate split method available for single-step case splitting. The effect of repeatedly applying (split thms) can be imitated by “(simp only: split: thms)”. 

The cong modifiers add or delete Simplifier congruence rules (see also §9.3.2); the default is to add. 

simp_all is similar to simp, but acts on all goals, working backwards from the last to the first one as usual in Isabelle.1 

Chained facts are inserted into all subgoals, before the simplification process starts. Further rule declarations are the same as for simp. 

The proof method fails if all subgoals remain unchanged after simplification. 

simp_depth_limit limits the number of recursive invocations of the Simplifier during conditional rewriting. 

By default the Simplifier methods above take local assumptions fully into account, using equational assumptions in the subsequent normalization process, or simplifying assumptions themselves. Further options allow to fine-tune the behavior of the Simplifier in this respect, corresponding to a variety of ML tactics as follows.2 

<table><tr><td>Isar method</td><td>ML tactic</td><td>behavior</td></tr><tr><td>(simp (no_asm))</td><td>simp_tac</td><td>assumptions are ignored completely</td></tr><tr><td>(simp (no_asm_simp))</td><td>asm_simp_tac</td><td>assumptions are used in the simplification of the conclusion but are not themselves simplified</td></tr><tr><td>(simp (no_asm_use))</td><td>full_simp_tac</td><td>assumptions are simplified but are not used in the simplification of each other or the conclusion</td></tr><tr><td>(simp)</td><td>asm_full_simp_tac</td><td>assumptions are used in the simplification of the conclusion and to simplify other assumptions</td></tr><tr><td>(simp (asm_lr))</td><td>asm_lr_simp_tac</td><td>compatibility mode: an assumption is only used for simplifying assumptions which are to the right of it</td></tr></table>

In Isabelle/Pure, proof methods simp and simp_all only know about metaequality ≡. Any new object-logic needs to re-define these methods via Simplifier.method_setup in ML: Isabelle/FOL or Isabelle/HOL may serve as blue-prints. 

# Examples

We consider basic algebraic simplifications in Isabelle/HOL. The rather trivial goal $0 + ( x + 0 ) = x + 0 + 0$ looks like a good candidate to be solved by a single call of simp: 

lemma $0 + ( x + 0 ) = x + 0 + 0$ apply simp? oops 

The above attempt fails, because 0 and $( + )$ in the HOL library are declared as generic type class operations, without stating any algebraic laws yet. More specific types are required to get access to certain standard simplifications of the theory context, e.g. like this: 

lemma fixes $x : : n a t$ shows $0 + ( x + 0 ) = x + 0 + 0$ by simp 

lemma fixes x :: int shows $0 + ( x + 0 ) = x + 0 + 0$ by simp 

lemma fixes x :: 0a :: monoid_add shows $0 + ( x + 0 ) = x + 0 + 0$ by simp 

In many cases, assumptions of a subgoal are also needed in the simplification process. For example: 

lemma fixes $x : : n a t$ shows $x = 0 \Longrightarrow x + x = 0$ by simp 

lemma fixes $x : : n a t$ assumes $x = 0$ shows $x + x = 0$ apply simp oops 

lemma fixes $x : : n a t$ assumes $x = 0$ shows $x + x = 0$ using assms by simp 

As seen above, local assumptions that shall contribute to simplification need to be part of the subgoal already, or indicated explicitly for use by the subsequent method invocation. Both too little or too much information can make simplification fail, for different reasons. 

In the next example the malicious assumption $\land x : : n a t . f x = g ( f ( g x ) )$ does not contribute to solve the problem, but makes the default simp method loop: the rewrite rule $f ~ { \overset { \triangledown } { : } } x \equiv g ~ ( f ~ ( g ~ { \overset { \triangledown } { : } } x ) )$ extracted from the assumption does not terminate. The Simplifier notices certain simple forms of nontermination, but not this one. The problem can be solved nonetheless, by ignoring assumptions via special options as explained before: 

lemma $( \bigwedge x { : } n a t . \ f \ x = g \ ( f \ ( g \ x ) ) ) \Longrightarrow f \ 0 = f \ 0 + 0$ 

by (simp (no_asm)) 

The latter form is typical for long unstructured proof scripts, where the control over the goal content is limited. In structured proofs it is usually better to avoid pushing too many facts into the goal state in the first place. Assumptions in the Isar proof context do not intrude the reasoning if not used explicitly. This is illustrated for a toplevel statement and a local proof body as follows: 

lemma 

assumes Vx::nat. f x = g (f (g x)) 

shows $f ~ 0 = f ~ 0 + 0$ by simp 

notepad 

begin 

assume $\land x : : n a t . \ f x = g \ ( f \ ( g \ x ) )$ 

have $f ~ 0 = f ~ 0 + 0$ by simp 

# end

Because assumptions may simplify each other, there can be very subtle cases of nontermination. For example, the regular simp method applied to $P$ $( f x )$ $\implies y = x \implies f x = f y \implies Q$ gives rise to the infinite reduction sequence 

$$
P (f x) \stackrel {f x \equiv f y} {\longmapsto} P (f y) \stackrel {y \equiv x} {\longmapsto} P (f x) \stackrel {f x \equiv f y} {\longmapsto} \dots
$$

whereas applying the same to $y \ = \ x \implies f \ x = f \ y \implies P$ $( f \ x ) \implies Q$ terminates (without solving the goal): 

lemma $y = x \Longrightarrow f x = f y \Longrightarrow P \left( f x \right) \Longrightarrow Q$ 

apply simp 

oops 

See also §9.3.4 for options to enable Simplifier trace mode, which often helps to diagnose problems with rewrite systems. 

# 9.3.2 Declaring rules

simp : attribute 

split : attribute 

cong : attribute 

print_simpset∗ : context → 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/355dc5e1a9741915bef3d8de9b022ac79e776af9558e76ebb17cae101018289c.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/32d4f02c62b0180ea78f98af005f1a2efa05896d444ad62e509aa7fcbde35476.jpg)


simp declares rewrite rules, by adding or deleting them from the simpset within the theory or proof context. Rewrite rules are theorems expressing some form of equality, for example: 

$$
S u c \ref {e q : 1} m + \ref {e q : 2} n = \ref {e q : 3} m + S u c \ref {e q : 4} n
$$

$$
? P \land ? P \longleftrightarrow ? P
$$

$$
? A \cup ? B \equiv \{x. x \in ? A \lor x \in ? B \}
$$

Conditional rewrites such as $\acute { z } m < \acute { z } n \Longrightarrow \acute { z } m$ div ? $\because n = 0$ are also permitted; the conditions can be arbitrary formulas. 

Internally, all rewrite rules are translated into Pure equalities, theorems with conclusion $l h s \equiv r h s$ . The simpset contains a function for extracting equalities from arbitrary theorems, which is usually installed when the object-logic is configured initially. For example, ¬ $\ell x \in \{ \}$ could be turned into ? $\{ x \in \{ \} \equiv F a l s e$ . Theorems that are declared as simp and local assumptions within a goal are treated uniformly in this respect. 

The Simplifier accepts the following formats for the lhs term: 

1. First-order patterns, considering the sublanguage of application of constant operators to variable operands, without $\lambda$ -abstractions or functional variables. For example: 

$$
(\ref {e q : 1}) + \ref {e q : 2} \equiv \ref {e q : 3} + (\ref {e q : 4})
$$

$$
f (f \ref {e q : 1} x \ref {e q : 2}) \ref {e q : 3} z \equiv f \ref {e q : 4} x (f \ref {e q : 5} y \ref {e q : 6})
$$

2. Higher-order patterns in the sense of [36]. These are terms in $\beta$ - normal form (this will always be the case unless you have done something strange) where each occurrence of an unknown is of the form ? $? F x _ { 1 } \ldots x _ { n }$ , where the $x _ { i }$ are distinct bound variables. For example, $( \forall x . \ { \overset { \triangledown } { \cdot } } \ Q P \ x \wedge \ { \overset { \triangledown } { \cdot } } Q \ x ) \equiv ( \forall x . \ { \overset { \triangledown } { \cdot } } \ Q P \ x ) \wedge ( \forall x . \ { \overset { \triangledown } { \cdot } } Q \ x )$ or its symmetric form, since the rhs is also a higher-order pattern. 

3. Physical first-order patterns over raw $\lambda$ -term structure without $\alpha \beta \eta$ -equality; abstractions and bound variables are treated like quasi-constant term material. 

For example, the rule ?f ?x ∈ range $\ell f = T r u e$ rewrites the term ${ \textit { g a } } \in \ r a n g e \ g$ $g$ to True, but will fail to match $g$ $, \ ( h \ b ) \in \ r a n g e$ $\left( \lambda x . \textit { g } \left( h \textit { x } \right) \right)$ . However, offending subterms (in our case $\it { ? } f \ \it { ! } \it { 2 . } x .$ , which is not a pattern) can be replaced by adding new variables and conditions like this: $\begin{array} { r } { { ? } y = \ { 2 } f \ { 2 } x \Longrightarrow \ { 2 } y \in r a n g e \ { ? } f = T r u e } \end{array}$ $\ell f = T r u e$ is acceptable as a conditional rewrite rule of the second category since conditions can be arbitrary terms. 

split declares case split rules. 

cong declares congruence rules to the Simplifier context. 

Congruence rules are equalities of the form 

$$
\ldots \Rightarrow f? x _ {1} \ldots ? x _ {n} = f? y _ {1} \ldots ? y _ {n}
$$

This controls the simplification of the arguments of $f$ . For example, some arguments can be simplified under additional assumptions: 

$$
\begin{array}{l} ? P _ {1} \longleftrightarrow ? Q _ {1} \Longrightarrow \\ \left(\ref {e q : 1} \right. \\ \left(\ref {e q : P _ {1}} \longrightarrow \ref {e q : P _ {2}}\right) \longleftrightarrow \left(\ref {e q : Q _ {1}} \longrightarrow \ref {e q : Q _ {2}}\right) \\ \end{array}
$$

Given this rule, the Simplifier assumes ? $' Q _ { 1 }$ and extracts rewrite rules from it when simplifying $\ell P _ { 2 }$ . Such local assumptions are effective for rewriting formulae such as $x = 0 \longrightarrow y + x = y$ . 

The following congruence rule for bounded quantifiers also supplies contextual information — about the bound variable: 

$$
\begin{array}{l} (\ref {e q : 1}) \Rightarrow \\ (\bigwedge x. x \in ? B \Longrightarrow ? P x \longleftrightarrow ? Q x) \Longrightarrow \\ (\forall x \in ? A. ? P x) \longleftrightarrow (\forall x \in ? B. ? Q x) \\ \end{array}
$$

This congruence rule for conditional expressions can supply contextual information for simplifying the arms: 

$$
\begin{array}{l} \ref {e q : p} = \ref {e q : q} \Longrightarrow \\ (\ref {e q : 1} \Rightarrow \ref {e q : 2}) \Longrightarrow \\ (\neg \ref {e q : 1} q \Longrightarrow \ref {e q : 2} b = \ref {e q : 3} d) \Longrightarrow \\ (i f? p t h e n? a e l s e? b) = (i f? q t h e n? c e l s e? d) \\ \end{array}
$$

A congruence rule can also prevent simplification of some arguments. Here is an alternative congruence rule for conditional expressions that conforms to non-strict functional evaluation: 

$$
\begin{array}{l} ? p = ? q \Longrightarrow \\ (i f \ref {i n s t a n t}) \\ \end{array}
$$

Only the first argument is simplified; the others remain unchanged. This can make simplification much faster, but may require an extra case split over the condition $\ell q$ to prove the goal. 

print_simpset prints the collection of rules declared to the Simplifier, which is also known as “simpset” internally; the “!” option indicates extra verbosity. 

The implicit simpset of the theory context is propagated monotonically through the theory hierarchy: forming a new theory, the union of the simpsets of its imports are taken as starting point. Also note that definitional packages like datatype, primrec, fun routinely declare Simplifier rules to the target context, while plain definition is an exception in not declaring anything. 

It is up the user to manipulate the current simpset further by explicitly adding or deleting theorems as simplification rules, or installing other tools via simplification procedures (§9.3.5). Good simpsets are hard to design. Rules that obviously simplify, like ? $\textit { z n } + \textit { 0 } \equiv \textit { ? n }$ are good candidates for the implicit simpset, unless a special non-normalizing behavior of certain operations is intended. More specific rules (such as distributive laws, which duplicate subterms) should be added only for specific proof steps. Conversely, sometimes a rule needs to be deleted just for some part of a proof. The need of frequent additions or deletions may indicate a poorly designed simpset. 

r The union of simpsets from theory imports (as described above) is not always : a good starting point for the new theory. If some ancestors have deleted simplification rules because they are no longer wanted, while others have left those rules in, then the union will contain the unwanted rules, and thus have to be deleted again in the theory body. 

# 9.3.3 Ordered rewriting with permutative rules

A rewrite rule is permutative if the left-hand side and right-hand side are the equal up to renaming of variables. The most common permutative rule is commutativity: ? $\mathit { z x } + \mathit { ? y } = \mathit { ? y } + \mathit { ? x }$ . Other examples include $( \it { ? } x \mathrm { ~ - ~ } \it { ? } y ) \gets$ ? $\mathit { z z } = ( \mathit { z x } - \mathit { ? z } ) - \mathit { ? y }$ in arithmetic and insert ? $\boldsymbol { \ell } \boldsymbol { x }$ (insert ?y ?A) = insert ? $\it { ? y }$ (insert ?x ?A) for sets. Such rules are common enough to merit special attention. 

Because ordinary rewriting loops given such rules, the Simplifier employs a special strategy, called ordered rewriting. Permutative rules are detected and only applied if the rewriting step decreases the redex wrt. a given term ordering. For example, commutativity rewrites $b + a$ to $a ~ + ~ b$ , but then 

stops, because the redex cannot be decreased further in the sense of the term ordering. 

The default is lexicographic ordering of term structure, but this could be also changed locally for special applications via Simplifier.set_term_ord in Isabelle/ML. 

Permutative rewrite rules are declared to the Simplifier just like other rewrite rules. Their special status is recognized automatically, and their application is guarded by the term ordering accordingly. 

# Rewriting with AC operators

Ordered rewriting is particularly effective in the case of associativecommutative operators. (Associativity by itself is not permutative.) When dealing with an AC-operator $f$ , keep the following points in mind: 

• The associative law must always be oriented from left to right, namely $f \ ( f x y ) \ z = f x \ ( f y z )$ $f$ . The opposite orientation, if used with commutativity, leads to looping in conjunction with the standard term order. 

• To complete your set of rewrite rules, you must add not just associativity (A) and commutativity (C) but also a derived rule leftcommutativity (LC): $f x \ ( f y \ z ) = f y \ ( f x \ z )$ . 

Ordered rewriting with the combination of A, C, and LC sorts a term lexicographically — the rewriting engine imitates bubble-sort. 

# experiment

fixes $f : : { ' a } \Rightarrow { ' a } \Rightarrow { ' a }$ (infix · 60) 

assumes assoc: $( x \cdot y ) \cdot z = x \cdot ( y \cdot z )$ 

assumes commute: $x \cdot y = y \cdot x$ 

# begin

lemma left_commute: $x \cdot ( y \cdot z ) = y \cdot ( x \cdot z )$ 

proof − 

have $( x \cdot y ) \cdot z = ( y \cdot x ) \cdot z$ by (simp only: commute) 

then show ?thesis by (simp only: assoc) 

# qed

lemmas AC_rules = assoc commute left_commute 

Thus the Simplifier is able to establish equalities with arbitrary permutations of subterms, by normalizing to a common standard form. For example: 

lemma $( b \cdot c ) \cdot a = x x x$ 

apply (simp only: AC_rules) 

1. $a \cdot ( b \cdot c ) = x x x$ 

oops 

lemma $( b \cdot c ) \cdot a = a \cdot ( b \cdot c )$ by (simp only: AC_rules) 

lemma $( b \cdot c ) \cdot a = c \cdot ( b \cdot a )$ by (simp only: AC_rules) 

lemma $( b \cdot c ) \cdot a = ( c \cdot b ) \cdot a$ by (simp only: AC_rules) 

# end

Martin and Nipkow [31] discuss the theory and give many examples; other algebraic structures are amenable to ordered rewriting, such as Boolean rings. The Boyer-Moore theorem prover [11] also employs ordered rewriting. 

# Re-orienting equalities

Another application of ordered rewriting uses the derived rule eq_commute: $\mathit { i } a = \mathit { i } b ) = ( \mathit { i } b = \mathit { i } a )$ to reverse equations. 

This is occasionally useful to re-orient local assumptions according to the term ordering, when other built-in mechanisms of reorientation and mutual simplification fail to apply. 

# 9.3.4 Simplifier tracing and debugging

simp_trace : attribute default false  
simp_trace_depth_limit : attribute default 1  
simp_DEBUG : attribute default false  
simp_trace_new : attribute  
simp_break : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/293b6ecce63113795e69deaae6dfecad0da6ec45a8f5e1b00cdd1eb6a086b833.jpg)


These attributes and configurations options control various aspects of Simplifier tracing and debugging. 

simp_trace makes the Simplifier output internal operations. This includes rewrite steps (but not traces from simproc calls), but also bookkeeping like modifications of the simpset. 

simp_trace_depth_limit limits the effect of simp_trace to the given depth of recursive Simplifier invocations (when solving conditions of rewrite rules). 

simp_debug makes the Simplifier output some extra information about internal operations. This includes any attempted invocation of simplification procedures and the corresponding traces. 

simp_trace_new controls Simplifier tracing within Isabelle/PIDE applications, notably Isabelle/jEdit [56]. This provides a hierarchical representation of the rewriting steps performed by the Simplifier. 

Users can configure the behaviour by specifying breakpoints, verbosity and enabling or disabling the interactive mode. In normal verbosity (the default), only rule applications matching a breakpoint will be shown to the user. In full verbosity, all rule applications will be logged. Interactive mode interrupts the normal flow of the Simplifier and defers the decision how to continue to the user via some GUI dialog. 

simp_break declares term or theorem breakpoints for simp_trace_new as described above. Term breakpoints are patterns which are checked for matches on the redex of a rule application. Theorem breakpoints trigger when the corresponding theorem is applied in a rewrite step. For example: 

declare conjI [simp_break] declare [[simp_break ?x ∧ ?y]] 

# 9.3.5 Simplification procedures

A simplification procedure or simproc is an ML function that produces proven rewrite rules on demand. Simprocs are guarded by multiple patterns for the left-hand sides of equations. The Simplifier first matches the current redex against one of the LHS patterns; if this succeeds, the corresponding ML function is invoked, passing the Simplifier context and redex term. The function may choose to succeed with a specific result for the redex, or fail. 

The successful result of a simproc needs to be a (possibly conditional) rewrite rule $t \equiv u$ that is applicable to the current redex. The rule will be applied just as any ordinary rewrite rule. It is expected to be already in internal form of the Pure logic, bypassing the automatic preprocessing of object-level equivalences. 

simplproc_setup : local_theory $\rightarrow$ local_theory  
simplproc_setup : ML antiquotation  
simplproc : attribute 

simproc_setup 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/79e245b91414601e7a02bb2097e78d23c41a0d3698da4b1f74af03c187ab814b.jpg)


simproc_setup_id 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fe2b287f9ff24ff9c09f7f39494fb32860b664b7dae9e965557f88d24efa9b4a.jpg)


patterns 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1a20422dbcf0fd73eef780254d9a01ae7d263864606bdfde06d9abb7334efce5.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7c209de874713cbdeadfad6c84ecb6551d77d91ac02914a7c278afec1b4968c2.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e1e952c1154004683974a7a0f7a121cf83342b707abe091342387b2126914a36.jpg)


Command simproc_setup defines a named simplification procedure that is invoked by the Simplifier whenever any of the given term patterns match the current redex. The implementation, which is provided as embedded ML source, needs to be of type morphism $- >$ Proof.context -> cterm $- >$ thm option, where the cterm represents the current redex $r$ and the result is supposed to be SOME proven rewrite rule $r \equiv r ^ { \prime }$ (or a generalized version); NONE indicates failure. The Proof.context argument holds the full context of the current Simplifier invocation. 

The morphism tells how to move from the abstract context of the original definition into the concrete context of applications. This is only relevant for simprocs that are defined “in” a local theory context (e.g. locale with later interpretation). 

By default, the simproc is declared to the current Simplifier context and thus active. The keyword passive avoids that: it merely defines a simproc that can be activated in a different context later on. 

ML antiquotation simproc_setup is like command simproc_setup, with slightly extended syntax following simproc_setup_id. It allows to introduce a new simproc conveniently within an ML module, and refer 

directly to its ML value. For example, see various uses in ~~/src/HOL/ Tools/record.ML. 

The optional identifier specifies characteristic theorems to distinguish simproc instances after application of morphisms, e.g. locale with multiple interpretation. See also the minimal example below. 

Attributes [simproc add: name] and [simproc del: name] add or delete named simprocs to the current Simplifier context. The default is to add a simproc. Note that simproc_setup already adds the new simproc by default, unless it specified as passive. 

# Examples

The following simplification procedure for $( \mathit { ? u } \colon \mathit { u n i t } ) \ = \ ( )$ in HOL performs fine-grained control over rule application, beyond higher-order pattern matching. Declaring unit_eq as simp directly would make the Simplifier loop! Note that a version of this simplification procedure is already active in Isabelle/HOL. 

```rust
simplproc_setup unit("x:::unit") = <K(K(fn ct => if HOLogic.is_unit(Thm.term_of ct) then NONE else SOME (mk_meta_eq @{thm unit_eq}))>> 
```

Since the Simplifier applies simplification procedures frequently, it is important to make the failure check in ML reasonably fast. 

The subsequent example shows how to define a local simproc with extra identifier to distinguish its instances after interpretation: 

locale loc = fixes x y :: 'a assumes eq: $x = y$ begin   
ML < simproc_setup<proc $(\mathbf{x}) =$ <fn phi $\Rightarrow$ fn $\Rightarrow$ fn $\Rightarrow$ SOME (Morphism.thm phi @{thm eq}>)identifier loc_axioms>   
> 

end 

# 9.3.6 Configurable Simplifier strategies

The core term-rewriting engine of the Simplifier is normally used in combination with some add-on components that modify the strategy and allow to integrate other non-Simplifier proof tools. These may be reconfigured in ML as explained below. Even if the default strategies of object-logics like Isabelle/HOL are used unchanged, it helps to understand how the standard Simplifier strategies work. 

# The subgoaler

```ocaml
Simplifier.set_subgoaler: (Proof.context -> int -> tactic) -> Proof.context -> Proof.context  
Simplifier.prems_of: Proof.context -> thm list 
```

The subgoaler is the tactic used to solve subgoals arising out of conditional rewrite rules or congruence rules. The default should be simplification itself. In rare situations, this strategy may need to be changed. For example, if the premise of a conditional rule is an instance of its conclusion, as in Suc ?m < ? $\acute { z } n \implies \acute { z } m < \acute { z } n$ , the default strategy could loop. 

```txt
Simplifier.set_subgoaler tac ctxt sets the subgoaler of the context to tac. The tactic will be applied to the context of the running Simplifier instance. 
```

Simplifier.prems_of ctxt retrieves the current set of premises from the context. This may be non-empty only if the Simplifier has been told to utilize local assumptions in the first place (cf. the options in §9.3.1). 

As an example, consider the following alternative subgoaler: 

```txt
ML_val < fun subgoaler_tac ctxt = assume_tac ctxt ORELSE' resolve_tac ctxt (Simplifier.prems_of ctxt) ORELSE' asm_simp_tac ctxt > 
```

This tactic first tries to solve the subgoal by assumption or by resolving with with one of the premises, calling simplification only if that fails. 

# The solver

```ocaml
type solver  
Simplifier.mkSolver: string -> (Proof.context -> int -> tactic) -> solver  
infix setSolver: Proof.context * solver -> Proof.context  
infix addSolver: Proof.context * solver -> Proof.context  
infix setSSolver: Proof.context * solver -> Proof.context  
infix addSSolver: Proof.context * solver -> Proof.context 
```

A solver is a tactic that attempts to solve a subgoal after simplification. Its core functionality is to prove trivial subgoals such as True and $t = t$ , but object-logics might be more ambitious. For example, Isabelle/HOL performs a restricted version of linear arithmetic here. 

Solvers are packaged up in abstract type solver, with Simplifier.mk_solver as the only operation to create a solver. 

Rewriting does not instantiate unknowns. For example, rewriting alone cannot prove $a \in \ \mathcal { Q } A$ since this requires instantiating ?A. The solver, however, is an arbitrary tactic and may instantiate unknowns as it pleases. This is the only way the Simplifier can handle a conditional rewrite rule whose condition contains extra variables. When a simplification tactic is to be combined with other provers, especially with the Classical Reasoner, it is important whether it can be considered safe or not. For this reason a simpset contains two solvers: safe and unsafe. 

The standard simplification strategy solely uses the unsafe solver, which is appropriate in most cases. For special applications where the simplification process is not allowed to instantiate unknowns within the goal, simplification starts with the safe solver, but may still apply the ordinary unsafe one in nested simplifications for conditional rules or congruences. Note that in this way the overall tactic is not totally safe: it may instantiate unknowns that appear also in other subgoals. 

Simplifier.mk_solver name tac turns tac into a solver; the name is only attached as a comment and has no further significance. 

ctxt setSSolver solver installs solver as the safe solver of ctxt. 

ctxt addSSolver solver adds solver as an additional safe solver; it will be tried after the solvers which had already been present in ctxt. 

ctxt setSolver solver installs solver as the unsafe solver of ctxt. 

ctxt addSolver solver adds solver as an additional unsafe solver; it will be tried after the solvers which had already been present in ctxt. 

The solver tactic is invoked with the context of the running Simplifier. Further operations may be used to retrieve relevant information, such as the list of local Simplifier premises via Simplifier.prems_of — this list may be non-empty only if the Simplifier runs in a mode that utilizes local assumptions (see also §9.3.1). The solver is also presented the full goal including its assumptions in any case. Thus it can use these (e.g. by calling assume_tac), even if the Simplifier proper happens to ignore local premises at the moment. 

As explained before, the subgoaler is also used to solve the premises of congruence rules. These are usually of the form $s = \ \ell x$ , where $s$ needs to be simplified and ? $\ell x$ needs to be instantiated with the result. Typically, the subgoaler will invoke the Simplifier at some point, which will eventually call the solver. For this reason, solver tactics must be prepared to solve goals of the form $t = \mathrm { ~ } \ell x$ , usually by reflexivity. In particular, reflexivity should be tried before any of the fancy automated proof tools. 

It may even happen that due to simplification the subgoal is no longer an equality. For example, $F a l s e \longleftrightarrow \ ? Q$ could be rewritten to ¬ ?Q. To cover this case, the solver could try resolving with the theorem ¬ False of the object-logic. 

If a premise of a congruence rule cannot be proved, then the congruence is : ignored. This should only happen if the rule is conditional — that is, contains premises not of the form $t = \ell x$ . Otherwise it indicates that some congruence rule, or possibly the subgoaler or solver, is faulty. 

# The looper

```ocaml
infix setloop: Proof.context * (Proof.context -> int -> tactic) -> Proof.context  
infix addloop: Proof.context * (string * (Proof.context -> int -> tactic)) -> Proof.context  
infix delloop: Proof.context * string -> Proof.context  
Splitter.add_split: thm -> Proof.context -> Proof.context  
Splitter.add_split: thm -> Proof.context -> Proof.context  
Splitter.add_split_bang: thm -> Proof.context -> Proof.context  
Splitter.del_split: thm -> Proof.context -> Proof.context 
```

The looper is a list of tactics that are applied after simplification, in case the solver failed to solve the simplified goal. If the looper succeeds, the simplification process is started all over again. Each of the subgoals generated by the looper is attacked in turn, in reverse order. 

A typical looper is case splitting: the expansion of a conditional. Another possibility is to apply an elimination rule on the assumptions. More adventurous loopers could start an induction. 

ctxt setloop tac installs tac as the only looper tactic of ctxt. 

ctxt addloop (name, tac) adds tac as an additional looper tactic with name name, which is significant for managing the collection of loopers. The tactic will be tried after the looper tactics that had already been present in ctxt. 

ctxt delloop name deletes the looper tactic that was associated with name from ctxt. 

Splitter.add_split thm ctxt adds split tactic for thm as additional looper tactic of ctxt (overwriting previous split tactic for the same constant). 

Splitter.add_split_bang thm ctxt adds aggressive (see §9.3.1) split tactic for thm as additional looper tactic of ctxt (overwriting previous split tactic for the same constant). 

Splitter.del_split thm ctxt deletes the split tactic corresponding to thm from the looper tactics of ctxt. 

The splitter replaces applications of a given function; the right-hand side of the replacement can be anything. For example, here is a splitting rule for conditional expressions: 

$$
? P (i f ? Q \text {?} x \text {?} y) \longleftrightarrow (\text {?} Q \longrightarrow \text {?} P \text {?} x) \wedge (\neg \text {?} Q \longrightarrow \text {?} P \text {?} y)
$$

Another example is the elimination operator for Cartesian products (which happens to be called case_prod in Isabelle/HOL: 

$$
? P \left(c a s e \_ p r o d ? f ? p\right) \longleftrightarrow (\forall a b. ? p = (a, b) \longrightarrow ? P (f a b))
$$

For technical reasons, there is a distinction between case splitting in the conclusion and in the premises of a subgoal. The former is done by Splitter.split_tac with rules like if_split or option.split, which do not 

split the subgoal, while the latter is done by Splitter.split_asm_tac with rules like if_split_asm or option.split_asm, which split the subgoal. The function Splitter.add_split automatically takes care of which tactic to call, analyzing the form of the rules given as argument; it is the same operation behind split attribute or method modifier syntax in the Isar source language. 

Case splits should be allowed only when necessary; they are expensive and hard to control. Case-splitting on if-expressions in the conclusion is usually beneficial, so it is enabled by default in Isabelle/HOL and Isabelle/FOL/ZF. 

! With Splitter.split_asm_tac as looper component, the Simplifier may split subgoals! This might cause unexpected problems in tactic expressions that silently assume 0 or 1 subgoals after simplification. 

# 9.3.7 Forward simplification

simplified : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/22b774ca1f2cb4d5ba404d2be79bff4495f0bc78cb0236ec4327d95ef54d9187.jpg)


opt 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/dd918bf10a65dfa75740b47a72efa85aceb9bb73095e017639d83633341f53aa.jpg)


simplified $a _ { 1 }$ . . . $a _ { n }$ causes a theorem to be simplified, either by exactly the specified rules $a _ { 1 }$ , . . . , $a _ { n }$ , or the implicit Simplifier context if no arguments are given. The result is fully simplified by default, including assumptions and conclusion; the options no_asm etc. tune the Simplifier in the same way as the for the simp method. 

Note that forward simplification restricts the Simplifier to its most basic operation of term rewriting; solver and looper tactics (§9.3.6) are not involved here. The simplified attribute should be only rarely required under normal circumstances. 

# 9.4 The Classical Reasoner

# 9.4.1 Basic concepts

Although Isabelle is generic, many users will be working in some extension of classical first-order logic. Isabelle/ZF is built upon theory FOL, while Isabelle/HOL conceptually contains first-order logic as a fragment. Theoremproving in predicate logic is undecidable, but many automated strategies have been developed to assist in this task. 

Isabelle’s classical reasoner is a generic package that accepts certain information about a logic and delivers a suite of automatic proof tools, based on rules that are classified and declared in the context. These proof procedures are slow and simplistic compared with high-end automated theorem provers, but they can save considerable time and effort in practice. They can prove theorems such as Pelletier’s [48] problems 40 and 41 in a few milliseconds (including full proof reconstruction): 

lemma $\begin{array} { r } { ( \exists y . \forall x . F x y \longleftrightarrow F x x ) \longrightarrow \neg ( \forall x . \exists y . \forall z . F z y \longleftrightarrow \neg F z x ) } \end{array}$ by blast 

lemma (∀ z . ∃ y. ∀ x . f x y ←→ f x z ∧ ¬ f x x ) −→ ¬ (∃ z . ∀ x . f x z ) by blast 

The proof tools are generic. They are not restricted to first-order logic, and have been heavily used in the development of the Isabelle/HOL library and applications. The tactics can be traced, and their components can be called directly; in this manner, any proof can be viewed interactively. 

# The sequent calculus

Isabelle supports natural deduction, which is easy to use for interactive proof. But natural deduction does not easily lend itself to automation, and has a bias towards intuitionism. For certain proofs in classical logic, it can not be called natural. The sequent calculus, a generalization of natural deduction, is easier to automate. 

A sequent has the form $\Gamma \vdash \Delta$ , where $\Gamma$ and $\Delta$ are sets of formulae.3 The sequent $P _ { 1 }$ , . . . , $P _ { m } \vdash Q _ { 1 }$ , . . . , $Q _ { n }$ is valid if $P _ { 1 }$ $P _ { 1 } \land \dotsc \land P _ { m }$ $P _ { m }$ implies $Q _ { 1 } \vee$ . . . ∨ $Q _ { n }$ . Thus $P _ { 1 }$ , . . . , $P _ { m }$ represent assumptions, each of which is true, while $Q _ { 1 }$ , . . . , $Q _ { n }$ represent alternative goals. A sequent is basic if its left 

and right sides have a common formula, as in $P$ , $Q \vdash Q$ , $R$ ; basic sequents are trivially valid. 

Sequent rules are classified as right or left, indicating which side of the ` symbol they operate on. Rules that operate on the right side are analogous to natural deduction’s introduction rules, and left rules are analogous to elimination rules. The sequent calculus analogue of $( \longrightarrow I )$ ) is the rule 

$$
\frac {P , \Gamma \vdash \Delta , Q}{\Gamma \vdash \Delta , P \longrightarrow Q} (\longrightarrow R)
$$

Applying the rule backwards, this breaks down some implication on the right side of a sequent; $\Gamma$ and $\Delta$ stand for the sets of formulae that are unaffected by the inference. The analogue of the pair (∨I 1) and (∨I 2) is the single rule 

$$
\frac {\Gamma \vdash \Delta , P , Q}{\Gamma \vdash \Delta , P \lor Q} (\lor R)
$$

This breaks down some disjunction on the right side, replacing it by both disjuncts. Thus, the sequent calculus is a kind of multiple-conclusion logic. 

To illustrate the use of multiple formulae on the right, let us prove the classical theorem ( $P \longrightarrow Q$ ) ∨ ( ${ \cal Q } \longrightarrow { \cal P }$ ). Working backwards, we reduce this formula to a basic sequent: 

$$
\begin{array}{l} \frac {P , Q \vdash Q , P}{P \vdash Q , (Q \longrightarrow P)} (\longrightarrow R) \\ \overline {{\vdash (P \longrightarrow Q) , (Q \longrightarrow P)}} \stackrel {T: \quad \text {e q .} (\text {e q .})} {\longrightarrow} R \\ \overline {{\vdash (P \longrightarrow Q) \vee (Q \longrightarrow P)}} (\lor R) \\ \end{array}
$$

This example is typical of the sequent calculus: start with the desired theorem and apply rules backwards in a fairly arbitrary manner. This yields a surprisingly effective proof procedure. Quantifiers add only few complications, since Isabelle handles parameters and schematic variables. See [47, Chapter 10] for further discussion. 

# Simulating sequents by natural deduction

Isabelle can represent sequents directly, as in the object-logic LK. But natural deduction is easier to work with, and most object-logics employ it. Fortunately, we can simulate the sequent $P _ { 1 }$ , . . . , $P _ { m } \vdash Q _ { 1 } , \ldots$ , $Q _ { n }$ by the Isabelle formula $P _ { 1 } \implies . . . \implies P _ { m } \implies \neg \ Q _ { 2 } \implies . . . \implies \neg \ Q _ { n } \implies Q _ { 1 }$ where the order of the assumptions and the choice of $Q _ { 1 }$ are arbitrary. Elim-resolution plays a key role in simulating sequent proofs. 

We can easily handle reasoning on the left. Elim-resolution with the rules $( \lor E )$ , $( \perp E )$ and $( \exists E )$ achieves a similar effect as the corresponding sequent rules. For the other connectives, we use sequent-style elimination rules instead of destruction rules such as $( \land E 1 , 2 )$ and $( \forall E )$ . But note that the rule $( \neg L )$ has no effect under our representation of sequents! 

$$
\frac {\Gamma \vdash \Delta , P}{\neg P , \Gamma \vdash \Delta} (\neg L)
$$

What about reasoning on the right? Introduction rules can only affect the formula in the conclusion, namely $Q _ { 1 }$ . The other right-side formulae are represented as negated assumptions, $\lnot \ Q _ { 2 }$ , $\ldots , \lnot \ Q _ { n }$ . In order to operate on one of these, it must first be exchanged with $Q _ { 1 }$ . Elim-resolution with the swap rule has this effect: $\lnot \ P \Longrightarrow ( \lnot \ R \Longrightarrow P ) \Longrightarrow R$ 

To ensure that swaps occur only when necessary, each introduction rule is converted into a swapped form: it is resolved with the second premise of (swap). The swapped form of $( \land I )$ , which might be called $( \neg \land E )$ , is 

$$
\neg (P \wedge Q) \Longrightarrow (\neg R \Longrightarrow P) \Longrightarrow (\neg R \Longrightarrow Q) \Longrightarrow R
$$

Similarly, the swapped form of ( $\longrightarrow I$ ) is 

$$
\neg (P \longrightarrow Q) \Longrightarrow (\neg R \Longrightarrow P \Longrightarrow Q) \Longrightarrow R
$$

Swapped introduction rules are applied using elim-resolution, which deletes the negated formula. Our representation of sequents also requires the use of ordinary introduction rules. If we had no regard for readability of intermediate goal states, we could treat the right side more uniformly by representing sequents as 

$$
P _ {1} \Longrightarrow \dots \Longrightarrow P _ {m} \Longrightarrow \neg Q _ {1} \Longrightarrow \dots \Longrightarrow \neg Q _ {n} \Longrightarrow \bot
$$

# Extra rules for the sequent calculus

As mentioned, destruction rules such as $( \land E 1 , 2 )$ and $( \forall E )$ must be replaced by sequent-style elimination rules. In addition, we need rules to embody the classical equivalence between $P \longrightarrow Q$ and ¬ P ∨ Q. The introduction rules (∨I 1, 2) are replaced by a rule that simulates $( \lor R )$ : 

$$
(\neg Q \Longrightarrow P) \Longrightarrow P \lor Q
$$

The destruction rule ( $\longrightarrow E$ ) is replaced by 

$$
(P \longrightarrow Q) \Longrightarrow (\neg P \Longrightarrow R) \Longrightarrow (Q \Longrightarrow R) \Longrightarrow R
$$

Quantifier replication also requires special rules. In classical logic, ∃ x. P x is equivalent to $\lnot \ ( \forall \ : x . \lnot \ P \ : x )$ ; the rules $( \exists R )$ and $( \forall L )$ are dual: 

$$
\frac {\Gamma \vdash \Delta , \exists x . P x , P t}{\Gamma \vdash \Delta , \exists x . P x} (\exists R) \qquad \frac {P t , \forall x . P x , \Gamma \vdash \Delta}{\forall x . P x , \Gamma \vdash \Delta} (\forall L)
$$

Thus both kinds of quantifier may be replicated. Theorems requiring multiple uses of a universal formula are easy to invent; consider 

$$
(\forall x. P x \longrightarrow P (f x)) \wedge P a \longrightarrow P (f ^ {n} a)
$$

for any $n > 1$ . Natural examples of the multiple use of an existential formula are rare; a standard one is ∃ x. ∀ y. $P \ x \longrightarrow P$ y . 

Forgoing quantifier replication loses completeness, but gains decidability, since the search space becomes finite. Many useful theorems can be proved without replication, and the search generally delivers its verdict in a reasonable time. To adopt this approach, represent the sequent rules $( \exists R )$ , $( \exists L )$ and $( \forall R )$ by $( \exists I )$ , $( \exists E )$ and $( \forall I )$ , respectively, and put $( \forall E )$ into elimination form: 

$$
\forall x. P x \Longrightarrow (P t \Longrightarrow Q) \Longrightarrow Q
$$

Elim-resolution with this rule will delete the universal formula after a single use. To replicate universal quantifiers, replace the rule by 

$$
\forall x. P x \Longrightarrow (P t \Longrightarrow \forall x. P x \Longrightarrow Q) \Longrightarrow Q
$$

To replicate existential quantifiers, replace (∃ I ) by 

$$
(\neg (\exists x. P x) \Longrightarrow P t) \Longrightarrow \exists x. P x
$$

All introduction rules mentioned above are also useful in swapped form. 

Replication makes the search space infinite; we must apply the rules with care. The classical reasoner distinguishes between safe and unsafe rules, applying the latter only when there is no alternative. Depth-first search may well go down a blind alley; best-first search is better behaved in an infinite search space. However, quantifier replication is too expensive to prove any but the simplest theorems. 

# 9.4.2 Rule declarations

The proof tools of the Classical Reasoner depend on collections of rules declared in the context, which are classified as introduction, elimination or destruction and as safe or unsafe. In general, safe rules can be attempted blindly, while unsafe rules must be used with care. A safe rule must never reduce a provable goal to an unprovable set of subgoals. 

The rule $P \Longrightarrow P \vee Q$ is unsafe because it reduces $P \lor Q$ to $P$ , which might turn out as premature choice of an unprovable subgoal. Any rule whose premises contain new unknowns is unsafe. The elimination rule $\forall x$ . $P$ $x \Longrightarrow$ $( P \ t \implies Q ) \implies Q$ is unsafe, since it is applied via elim-resolution, which discards the assumption $\forall x$ . $P$ $x$ and replaces it by the weaker assumption $P$ $t$ . The rule $^ { ) } t \implies \exists x$ . P $x$ is unsafe for similar reasons. The quantifier duplication rule $\forall x$ . P $x \Longrightarrow$ ( $P \ t \implies \forall x . \ P x \implies Q ) \implies Q$ is unsafe in a different sense: since it keeps the assumption $\forall x$ . $P$ $x$ , it is prone to looping. In classical first-order logic, all rules are safe except those mentioned above. The safe / unsafe distinction is vague, and may be regarded merely as a way of giving some rules priority over others. One could argue that $( \lor E )$ is unsafe, because repeated application of it could generate exponentially many subgoals. Induction rules are unsafe because inductive proofs are difficult to set up automatically. Any inference that instantiates an unknown in the proof state is unsafe — thus matching must be used, rather than unification. Even proof by assumption is unsafe if it instantiates unknowns shared with other subgoals. 

```txt
print_claset* : context →  
intro : attribute  
elim : attribute  
dest : attribute  
rule : attribute  
iff : attribute  
swapped : attribute 
```

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b0ae561e56eff0ef2b6f0434d4f9119f536502f277aa995e5a144a5d91db0309.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c357d5130d99fdeb6f400746024edb7d962e789b48e0636d09f77a99ff060716.jpg)


print_claset prints the collection of rules declared to the Classical Reasoner, i.e. the claset within the context. 

intro, elim, and dest declare introduction, elimination, and destruction rules, respectively. By default, rules are considered as unsafe (i.e. not applied blindly without backtracking), while “!” classifies as safe. Rule declarations marked by “?” coincide with those of Isabelle/Pure, cf. §6.4.3 (i.e. are only applied in single steps of the rule method). The optional natural number specifies an explicit weight argument, which is ignored by the automated reasoning tools, but determines the search order of single rule steps. 

Introduction rules are those that can be applied using ordinary resolution. Their swapped forms are generated internally, which will be applied using elim-resolution. Elimination rules are applied using elimresolution. Rules are sorted by the number of new subgoals they will yield; rules that generate the fewest subgoals will be tried first. Otherwise, later declarations take precedence over earlier ones. 

Rules already present in the context with the same classification are ignored. A warning is printed if the rule has already been added with some other classification, but the rule is added anyway as requested. 

rule del deletes all occurrences of a rule from the classical context, regardless of its classification as introduction / elimination / destruction and safe / unsafe. 

iff declares logical equivalences to the Simplifier and the Classical reasoner at the same time. Non-conditional rules result in a safe introduction and elimination pair; conditional ones are considered unsafe. Rules with negative conclusion are automatically inverted (using ¬- elimination internally). 

The “?” version of iff declares rules to the Isabelle/Pure context only, and omits the Simplifier declaration. 

swapped turns an introduction rule into an elimination, by resolving with the classical swap principle $\neg \ P \Longrightarrow ( \neg \ R \Longrightarrow P ) \Longrightarrow R$ in the second position. This is mainly for illustrative purposes: the Classical Reasoner already swaps rules internally as explained above. 

# 9.4.3 Structured methods

rule : method contradiction : method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a9497bfc06468a5627a865b3461eebdb48212912f4be517a336fb3a51431d966.jpg)


rule as offered by the Classical Reasoner is a refinement over the Pure one (see §6.4.3). Both versions work the same, but the classical version observes the classical rule context in addition to that of Isabelle/Pure. Common object logics (HOL, ZF, etc.) declare a rich collection of classical rules (even if these would qualify as intuitionistic ones), but only few declarations to the rule context of Isabelle/Pure (§6.4.3). 

contradiction solves some goal by contradiction, deriving any result from both ¬ A and $A$ . Chained facts, which are guaranteed to participate, may appear in either order. 

# 9.4.4 Fully automated methods

```txt
blast : method  
auto : method  
force : method  
fast : method  
slow : method  
best : method  
tforce : method  
vsimp : method  
tsimp : method  
eepen : method 
```

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/36841d2f1f934c3b14cdc7ccabfbe7a02b471ed827d0eed0b66551c95db7f802.jpg)


# clasimpmod

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/4ac056f7886eafa29fb112468ae7bd5e91c9d06b710d9cc60362b9a457a4c18c.jpg)


blast is a separate classical tableau prover that uses the same classical rule declarations as explained before. 

Proof search is coded directly in ML using special data structures. A successful proof is then reconstructed using regular Isabelle inferences. It is faster and more powerful than the other classical reasoning tools, 

but has major limitations too. 

• It does not use the classical wrapper tacticals, such as the integration with the Simplifier of fastforce. 

• It does not perform higher-order unification, as needed by the rule ? $\mathcal { Y } \ \stackrel { \mathcal { ? } } { : } \mathcal { X } \ \in \ r a n g e$ ? $\ell f$ in HOL. There are often alternatives to such rules, for example ? $\mathit { ? b } = \mathit { ? f } \mathit { ? x } \Longrightarrow \mathit { ? b } \in \mathit { r a n g e } \mathit { ? f } .$ . 

• Function variables may only be applied to parameters of the subgoal. (This restriction arises because the prover does not use higher-order unification.) If other function variables are present then the prover will fail with the message 

Function unknown’s argument not a bound variable 

• Its proof strategy is more general than fast but can be slower. If blast fails or seems to be running forever, try fast and the other proof tools described below. 

The optional integer argument specifies a bound for the number of unsafe steps used in a proof. By default, blast starts with a bound of 0 and increases it successively to 20. In contrast, (blast lim) tries to prove the goal using a search bound of lim. Sometimes a slow proof using blast can be made much faster by supplying the successful search bound to this proof method instead. 

auto combines classical reasoning with simplification. It is intended for situations where there are a lot of mostly trivial subgoals; it proves all the easy ones, leaving the ones it cannot prove. Occasionally, attempting to prove the hard ones may take a long time. 

The optional depth arguments in (auto m n) refer to its builtin classical reasoning procedures: m (default 4) is for blast, which is tried first, and $n$ (default 2) is for a slower but more general alternative that also takes wrappers into account. 

force is intended to prove the first subgoal completely, using many fancy proof tools and performing a rather exhaustive search. As a result, proof attempts may take rather long or diverge easily. 

fast, best, slow attempt to prove the first subgoal using sequent-style reasoning as explained before. Unlike blast, they construct proofs directly in Isabelle. 

There is a difference in search strategy and back-tracking: fast uses depth-first search and best uses best-first search (guided by a heuristic function: normally the total size of the proof state). 

Method slow is like fast, but conducts a broader search: it may, when backtracking from a failed proof attempt, undo even the step of proving a subgoal by assumption. 

fastforce, slowsimp, bestsimp are like fast, slow, best, respectively, but use the Simplifier as additional wrapper. The name fastforce, reflects the behaviour of this popular method better without requiring an understanding of its implementation. 

deepen works by exhaustive search up to a certain depth. The start depth is 4 (unless specified explicitly), and the depth is increased iteratively up to 10. Unsafe rules are modified to preserve the formula they act on, so that it be used repeatedly. This method can prove more goals than fast, but is much slower, for example if the assumptions have many universal quantifiers. 

Any of the above methods support additional modifiers of the context of classical (and simplifier) rules, but the ones related to the Simplifier are explicitly prefixed by simp here. The semantics of these ad-hoc rule declarations is analogous to the attributes given before. Facts provided by forward chaining are inserted into the goal before commencing proof search. 

# 9.4.5 Partially automated methods

These proof methods may help in situations when the fully-automated tools fail. The result is a simpler subgoal that can be tackled by other means, such as by manual instantiation of quantifiers. 

```yaml
safe : method
clarify : method
clarsimp : method 
```

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2daf981ac57c577de584f10ef032558207f3a92f4f0e1bd5ebc83548be66ea74.jpg)


clarsimp 

clasimpmod 

safe repeatedly performs safe steps on all subgoals. It is deterministic, with at most one outcome. 

clarify performs a series of safe steps without splitting subgoals; see also clarify_step. 

clarsimp acts like clarify, but also does simplification. Note that if the Simplifier context includes a splitter for the premises, the subgoal may still be split. 

# 9.4.6 Single-step tactics

safe_step : method 

inst_step : method 

step : method 

slow_step : method 

clarify_step : method 

These are the primitive tactics behind the automated proof methods of the Classical Reasoner. By calling them yourself, you can execute these procedures one step at a time. 

safe_step performs a safe step on the first subgoal. The safe wrapper tacticals are applied to a tactic that may include proof by assumption or Modus Ponens (taking care not to instantiate unknowns), or substitution. 

inst_step is like safe_step, but allows unknowns to be instantiated. 

step is the basic step of the proof procedure, it operates on the first subgoal. The unsafe wrapper tacticals are applied to a tactic that tries safe, inst_step, or applies an unsafe rule from the context. 

slow_step resembles step, but allows backtracking between using safe rules with instantiation (inst_step) and using unsafe rules. The resulting search space is larger. 

clarify_step performs a safe step on the first subgoal; no splitting step is applied. For example, the subgoal $A \land B$ is left as a conjunction. Proof by assumption, Modus Ponens, etc., may be performed provided they do not instantiate unknowns. Assumptions of the form $x = t$ may be eliminated. The safe wrapper tactical is applied. 

# 9.4.7 Modifying the search step

type wrapper $=$ (int -> tactic) -> (int -> tactic)   
infix addSWrapper: Proof.context \* (string \* (Proof.context -> wrapper)) -> Proof.context   
infix addSbefore: Proof.context \* (string \* (Proof.context -> int -> tactic)) -> Proof.context   
infix addSafter: Proof.context \* (string \* (Proof.context -> int -> tactic)) -> Proof.context   
infix delSWrapper: Proof.context \* string -> Proof.context   
infix addWrapper: Proof.context \* (string \* (Proof.context -> wrapper)) -> Proof.context   
infix addbefore: Proof.context \* (string \* (Proof.context -> int -> tactic)) -> Proof.context   
infix addafter: Proof.context \* (string \* (Proof.context -> int -> tactic)) -> Proof.context   
infix delWrapper: Proof.context \* string -> Proof.context   
addSss: Proof.context -> Proof.context   
addss: Proof.context -> Proof.context 

The proof strategy of the Classical Reasoner is simple. Perform as many safe inferences as possible; or else, apply certain safe rules, allowing instantiation of unknowns; or else, apply an unsafe rule. The tactics also eliminate assumptions of the form $x = t$ by substitution if they have been set up to do so. They may perform a form of Modus Ponens: if there are assumptions $P$ $\longrightarrow Q$ and $P$ , then replace $P \longrightarrow Q$ by $Q$ . 

The classical reasoning tools — except blast — allow to modify this basic proof strategy by applying two lists of arbitrary wrapper tacticals to it. The first wrapper list, which is considered to contain safe wrappers only, affects safe_step and all the tactics that call it. The second one, which may contain unsafe wrappers, affects the unsafe parts of step, slow_step, and the tactics that call them. A wrapper transforms each step of the search, for example by attempting other tactics before or after the original step tactic. All members of a wrapper list are applied in turn to the respective step tactic. 

Initially the two wrapper lists are empty, which means no modification of the step tactics. Safe and unsafe wrappers are added to the context with the functions given below, supplying them with wrapper names. These names may be used to selectively delete wrappers. 

ctxt addSWrapper (name, wrapper) adds a new wrapper, which should yield a safe tactic, to modify the existing safe step tactic. 

ctxt addSbefore (name, tac) adds the given tactic as a safe wrapper, such that it is tried before each safe step of the search. 

ctxt addSafter (name, tac) adds the given tactic as a safe wrapper, such that it is tried when a safe step of the search would fail. 

ctxt delSWrapper name deletes the safe wrapper with the given name. 

ctxt addWrapper (name, wrapper) adds a new wrapper to modify the existing (unsafe) step tactic. 

ctxt addbefore (name, tac) adds the given tactic as an unsafe wrapper, such that it its result is concatenated before the result of each unsafe step. 

ctxt addafter (name, tac) adds the given tactic as an unsafe wrapper, such that it its result is concatenated after the result of each unsafe step. 

ctxt delWrapper name deletes the unsafe wrapper with the given name. 

addSss adds the simpset of the context to its classical set. The assumptions and goal will be simplified, in a rather safe way, after each safe step of the search. 

addss adds the simpset of the context to its classical set. The assumptions and goal will be simplified, before the each unsafe step of the search. 

# 9.5 Object-logic setup

judgment : theory → theory 

atomize : method 

atomize : attribute 

rule_format : attribute 

rulify : attribute 

The very starting point for any Isabelle object-logic is a “truth judgment” that links object-level statements to the meta-logic (with its minimal language of prop that covers universal quantification $\Lambda$ and implication $\Longrightarrow$ ). 

Common object-logics are sufficiently expressive to internalize rule statements over $\Lambda$ and =⇒ within their own language. This is useful in certain situations where a rule needs to be viewed as an atomic statement from the meta-level perspective, e.g. $\Lambda x$ . $x \in A \Longrightarrow P x$ versus $\forall x \in A$ . $P$ x . 

From the following language elements, only the atomize method and rule_format attribute are occasionally required by end-users, the rest is for those who need to setup their own object-logic. In the latter case existing formulations of Isabelle/FOL or Isabelle/HOL may be taken as realistic examples. 

Generic tools may refer to the information provided by object-logic declarations internally. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/3b834b0c782ffc925585554d981d55aa081422bac7d6421344c4d586d3f82bad.jpg)


judgment c :: σ (mx) declares constant $c$ as the truth judgment of the current object-logic. Its type $\sigma$ should specify a coercion of the category of object-level propositions to prop of the Pure meta-logic; the mixfix annotation $( m x )$ would typically just link the object language (internally of syntactic category logic) with that of prop. Only one judgment declaration may be given in any theory development. 

atomize (as a method) rewrites any non-atomic premises of a sub-goal, using the meta-level equations declared via atomize (as an attribute) beforehand. As a result, heavily nested goals become amenable to fundamental operations such as resolution (cf. the rule method). Giving the “ $( f u l l ) ^ { \dag }$ option here means to turn the whole subgoal into an 

object-statement (if possible), including the outermost parameters and assumptions as well. 

A typical collection of atomize rules for a particular object-logic would provide an internalization for each of the connectives of $\Lambda , \Longrightarrow$ , and ≡. Meta-level conjunction should be covered as well (this is particularly important for locales, see §5.7). 

rule_format rewrites a theorem by the equalities declared as rulify rules in the current object-logic. By default, the result is fully normalized, including assumptions and conclusions at any depth. The (no_asm) option restricts the transformation to the conclusion of a rule. 

In common object-logics (HOL, FOL, ZF), the effect of rule_format is to replace (bounded) universal quantification (∀ ) and implication ( $\longrightarrow$ ) by the corresponding rule statements over V and =⇒. 

# 9.6 Tracing higher-order unification

unify_trace : attribute default false 

unify_trace_simp : attribute default false 

unify_trace_types : attribute default false 

unify_trace_bound : attribute default 50 

unify_search_bound : attribute default 60 

Higher-order unification works well in most practical situations, but sometimes needs extra care to identify problems. These tracing options may help. 

unify_trace controls whether unify trace messages will be printed (controlled via more fine-grained tracing options below). 

unify_trace_simp controls tracing of the simplification phase of higherorder unification. 

unify_trace_types controls tracing of potential incompleteness, when unification is not considering all possible instantiations of schematic type variables. 

unify_trace_bound determines the depth where unification starts to print tracing information once it reaches depth; 0 for full tracing. At the default value, tracing information is almost never printed in practice. 

unify_search_bound prevents unification from searching past the given depth. Because of this bound, higher-order unification cannot return an infinite sequence, though it can return an exponentially long one. The search rarely approaches the default value in practice. If the search is cut off, unification prints a warning “Unification bound exceeded”. 

Options for unification cannot be modified in a local context. Only the global • theory content is taken into account. 

# Part III

# Isabelle/HOL

# Higher-Order Logic

Isabelle/HOL is based on Higher-Order Logic, a polymorphic version of Church’s Simple Theory of Types. HOL can be best understood as a simplytyped version of classical set theory. The logic was first implemented in Gordon’s HOL system [20]. It extends Church’s original logic [14] by explicit type variables (naive polymorphism) and a sound axiomatization scheme for new types based on subsets of existing types. 

Andrews’s book [1] is a full description of the original Church-style higherorder logic, with proofs of correctness and completeness wrt. certain settheoretic interpretations. The particular extensions of Gordon-style HOL are explained semantically in two chapters of the 1993 HOL book [50]. 

Experience with HOL over decades has demonstrated that higher-order logic is widely applicable in many areas of mathematics and computer science. In a sense, Higher-Order Logic is simpler than First-Order Logic, because there are fewer restrictions and special cases. Note that HOL is weaker than FOL with axioms for ZF set theory, which is traditionally considered the standard foundation of regular mathematics, but for most applications this does not matter. If you prefer ML to Lisp, you will probably prefer HOL to ZF. 

The syntax of HOL follows $\lambda$ -calculus and functional programming. Function application is curried. To apply the function $f$ of type $\tau _ { 1 } \Rightarrow \tau _ { 2 } \Rightarrow \tau _ { 3 }$ to the arguments $a$ and $b$ in HOL, you simply write $f a b$ $b$ (as in ML or Haskell). There is no “apply” operator; the existing application of the Pure $\lambda$ -calculus is re-used. Note that in HOL $f \ ( a , \ b )$ $f$ means $^ { 6 6 } f$ applied to the pair $( a , \ b )$ (which is notation for Pair a $b$ ). The latter typically introduces extra formal efforts that can be avoided by currying functions by default. Explicit tuples are as infrequent in HOL formalizations as in good ML or Haskell programs. 

Isabelle/HOL has a distinct feel, compared to other object-logics like Isabelle/ZF. It identifies object-level types with meta-level types, taking advantage of the default type-inference mechanism of Isabelle/Pure. HOL fully identifies object-level functions with meta-level functions, with native abstraction and application. 

These identifications allow Isabelle to support HOL particularly nicely, but they also mean that HOL requires some sophistication from the user. In particular, an understanding of Hindley-Milner type-inference with type-classes, which are both used extensively in the standard libraries and applications. 

# Derived specification elements

# 11.1 Inductive and coinductive definitions

inductive : local_theory → local_theory 

inductive_set : local_theory local_theory 

coinductive : local_theory local_theory 

coinductive_set : local_theory local_theory 

print_inductives∗ : context → 

mono : attribute 

An inductive definition specifies the least predicate or set $R$ closed under given rules: applying a rule to elements of $R$ yields a result within $R$ . For example, a structural operational semantics is an inductive definition of an evaluation relation. 

Dually, a coinductive definition specifies the greatest predicate or set $R$ that is consistent with given rules: every element of $R$ can be seen as arising by applying a rule to elements of $R$ . An important example is using bisimulation relations to formalise equivalence of processes and infinite data structures. 

Both inductive and coinductive definitions are based on the Knaster-Tarski fixed-point theorem for complete lattices. The collection of introduction rules given by the user determines a functor on subsets of set-theoretic relations. The required monotonicity of the recursion scheme is proven as a prerequisite to the fixed-point definition and the resulting consequences. This works by pushing inclusion through logical connectives and any other operator that might be wrapped around recursive occurrences of the defined relation: there must be a monotonicity theorem of the form $A \leq B \Longrightarrow { \mathcal { M } } \ A \leq { \mathcal { M } } \ B$ , for each premise $\mathcal { M }$ R $t$ in an introduction rule. The default rule declarations of Isabelle/HOL already take care of most common situations. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ea3f2b66dab08267a3a63d6b46f3d90fa5dbb5acb1ac90fe2db54ad66b57107a.jpg)


inductive and coinductive define (co)inductive predicates from the introduction rules. 

The propositions given as clauses in the where part are either rules of the usual $\Lambda / { \Longrightarrow }$ format (with arbitrary nesting), or equalities using $=$ . The latter specifies extra-logical abbreviations in the sense of abbreviation. Introducing abstract syntax simultaneously with the actual introduction rules is occasionally useful for complex specifications. 

The optional for part contains a list of parameters of the (co)inductive predicates that remain fixed throughout the definition, in contrast to arguments of the relation that may vary in each occurrence within the given clauses. 

The optional monos declaration contains additional monotonicity theorems, which are required for each operator applied to a recursive set in the introduction rules. 

inductive_set and coinductive_set are wrappers for to the previous commands for native HOL predicates. This allows to define (co)inductive sets, where multiple arguments are simulated via tuples. 

print_inductives prints (co)inductive definitions and monotonicity rules; the “!” option indicates extra verbosity. 

mono declares monotonicity rules in the context. These rule are involved in the automated monotonicity proof of the above inductive and coinductive definitions. 

# 11.1.1 Derived rules

A (co)inductive definition of $R$ provides the following main theorems: 

R.intros is the list of introduction rules as proven theorems, for the recursive predicates (or sets). The rules are also available individually, using the names given them in the theory file; 

R.cases is the case analysis (or elimination) rule; 

R.induct or R.coinduct is the (co)induction rule; 

R.simps is the equation unrolling the fixpoint of the predicate one step. 

When several predicates $R _ { 1 }$ , . . . , $R _ { n }$ are defined simultaneously, the list of introduction rules is called $R _ { 1 \_ } . . . \_ R _ { n } . i n t r o s$ , the case analysis rules are called $R _ { 1 }$ .cases, . . . , $R _ { n } . c a s e s$ , and the list of mutual induction rules is called $R _ { 1 \_ \cdots \_ { n } }$ $R _ { n }$ .inducts. 

# 11.1.2 Monotonicity theorems

The context maintains a default set of theorems that are used in monotonicity proofs. New rules can be declared via the mono attribute. See the main Isabelle/HOL sources for some examples. The general format of such monotonicity theorems is as follows: 

• Theorems of the form $A \leq B \Longrightarrow \mathcal { M } \ A \leq \mathcal { M } \ B$ , for proving monotonicity of inductive definitions whose introduction rules have premises involving terms such as $\textit { M R t }$ . 

• Monotonicity theorems for logical operators, which are of the general form $( \dotsb \longrightarrow \dotsb ) \Longrightarrow \dotsb ( \dotsb \longrightarrow \dotsb ) \Longrightarrow \dotsb \longrightarrow \dotsb .$ . For example, in the case of the operator ∨, the corresponding theorem is 

$$
\begin{array}{c} P _ {1} \longrightarrow Q _ {1} P _ {2} \longrightarrow Q _ {2} \\ \hline P _ {1} \lor P _ {2} \longrightarrow Q _ {1} \lor Q _ {2} \end{array}
$$

• De Morgan style equations for reasoning about the “polarity” of expressions, e.g. 

$$
\neg \neg P \longleftrightarrow P \qquad \neg (P \land Q) \longleftrightarrow \neg P \lor \neg Q
$$

• Equations for reducing complex operators to more primitive ones whose monotonicity can easily be proved, e.g. 

$$
(P \longrightarrow Q) \longleftrightarrow \neg P \lor Q \qquad B a l l A P \equiv \forall x. x \in A \longrightarrow P x
$$

# Examples

The finite powerset operator can be defined inductively like this: 

inductive_set Fin :: 0a set ⇒ 0a set set for $A : \iota _ { a }$ set where 

empty: $\{ \} \in F i n ~ A$ | insert: $a \in A \Longrightarrow B \in F i n \ A \Longrightarrow i n s e r t \ a \ B \in F i n \ A$ 

The accessible part of a relation is defined as follows: 

inductive acc :: (0a ⇒ 0a ⇒ bool) ⇒ 0a ⇒ bool 

for $r : : { \mathit { \Delta } } a \Rightarrow { \mathit { \Delta } } ^ { \prime } a \Rightarrow b o o l$ (infix ≺ 50) 

where acc: ( $\bigwedge y . \ y \prec x \Longrightarrow a c c r y ) \Longrightarrow a c c r x$ 

Common logical connectives can be easily characterized as non-recursive inductive definitions with parameters, but without arguments. 

inductive AND for $A \ B : : \ b o o l$ 

where $A \Longrightarrow B \Longrightarrow A N D ~ A ~ B$ 

inductive OR for A B :: bool 

where $A \Longrightarrow O R \ A B$ 

| $B \Longrightarrow { \cal O R } \ : A \ : B$ 

inductive EXISTS for $B : : { } ^ { \prime } a \Rightarrow b o o l$ 

where $\textit { B a } \Longrightarrow \mathit { E X I S T S } \mathit { B }$ 

Here the cases or induct rules produced by the inductive package coincide with the expected elimination rules for Natural Deduction. Already in the original article by Gerhard Gentzen [18] there is a hint that each connective can be characterized by its introductions, and the elimination can be constructed systematically. 

# 11.2 Recursive functions

primrec : local_theory local_theory 

fun : local_theory local_theory 

function : local_theory → proof (prove) 

termination : local_theory → proof (prove) 

fun_cases : local_theory local_theory 

primrec specification 

fun 

function 

opts 

specification 

opts 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b9f73f540c0a711bd327c09469763cacc00a9e62634dd9407f5667ac01913e29.jpg)


sequential 

domintros 

termination 

term 

fun_cases 

thmdecl 

and 

prop 

primrec defines primitive recursive functions over datatypes (see also datatype). The given equations specify reduction rules that are produced by instantiating the generic combinator for primitive recursion that is available for each datatype. 

Each equation needs to be of the form: 

$$
f x _ {1} \dots x _ {m} (C y _ {1} \dots y _ {k}) z _ {1} \dots z _ {n} = r h s
$$

such that $C$ is a datatype constructor, rhs contains only the free variables on the left-hand side (or from the context), and all recursive occurrences of $f$ in rhs are of the form $f$ . . . yi . . . for some $i$ . At most one reduction rule for each constructor can be given. The order does not matter. For missing constructors, the function is defined to return a default value, but this equation is made difficult to access for users. 

The reduction rules are declared as simp by default, which enables standard proof methods like simp and auto to normalize expressions of $f$ applied to datatype constructions, by simulating symbolic computation via rewriting. 

function defines functions by general wellfounded recursion. A detailed description with examples can be found in [25]. The function is specified by a set of (possibly conditional) recursive equations with arbitrary pattern matching. The command generates proof obligations for the completeness and the compatibility of patterns. 

The defined function is considered partial, and the resulting simplification rules (named $f$ .psimps) and induction rule (named $f$ .pinduct) are guarded by a generated domain predicate $\underline { { f } } \_ d o m$ . The termination command can then be used to establish that the function is total. 

fun is a shorthand notation for “function (sequential)”, followed by automated proof attempts regarding pattern matching and termination. See [25] for further details. 

termination $f$ commences a termination proof for the previously defined function $f$ . If this is omitted, the command refers to the most recent function definition. After the proof is closed, the recursive equations and the induction principle is established. 

fun_cases generates specialized elimination rules for function equations. It expects one or more function equations and produces rules that eliminate the given equalities, following the cases given in the function definition. 

Recursive definitions introduced by the function command accommodate reasoning by induction (cf. induct): rule $f$ .induct refers to a specific induction rule, with parameters named according to the user-specified equations. Cases are numbered starting from 1. For primrec, the induction principle coincides with structural recursion on the datatype where the recursion is carried out. The equations provided by these packages may be referred later as theorem list $f$ .simps, where $f$ is the (collective) name of the functions defined. Individual equations may be named explicitly as well. 

The function command accepts the following options. 

sequential enables a preprocessor which disambiguates overlapping patterns by making them mutually disjoint. Earlier equations take precedence over later ones. This allows to give the specification in a format very similar to functional programming. Note that the resulting simplification and induction rules correspond to the transformed specification, not the one given originally. This usually means that each equation given by the user may result in several theorems. Also note that this automatic transformation only works for ML-style datatype patterns. 

domintros enables the automated generation of introduction rules for the domain predicate. While mostly not needed, they can be helpful in some proofs about partial functions. 

# Example: evaluation of expressions

Subsequently, we define mutual datatypes for arithmetic and boolean expressions, and use primrec for evaluation functions that follow the same recursive structure. 

```txt
datatype 'a aexp =  
IF 'a bexp 'a aexp 'a aexp  
| Sum 'a aexp 'a aexp  
| Diff 'a aexp 'a aexp  
| Var 'a  
| Num nat  
and 'a bexp =  
Less 'a aexp 'a aexp  
| And 'a bexp 'a bexp  
| Neg 'a bexp 
```

Evaluation of arithmetic and boolean expressions 

primrec evala :: (0a ⇒ nat) ⇒ 0a aexp ⇒ nat 

and evalb :: $( ^ { \prime } a \Rightarrow n a t ) \Rightarrow ^ { \prime } a \ b e x p \Rightarrow b o o l$ 

# where

evala env (IF b a1 a2) = (if evalb env b then evala env a1 else evala env a2) 

| evala env (Sum a1 a2) = evala env a1 $+$ evala env a2 

evala env (Diff a1 a2) = evala env a1 − evala env a2 

evala env $( \textit { V a r v } ) \ : = \ : e n v \ : v$ 

evala env $( N u m \ n ) = n$ 

evalb env (Less a1 a2) = (evala env a1 < evala env a2) 

evalb env (And b1 b2) = (evalb env b1 ∧ evalb env b2) 

evalb env (Neg b) = (¬ evalb env b) 

Since the value of an expression depends on the value of its variables, the functions evala and evalb take an additional parameter, an environment that maps variables to their values. 

Substitution on expressions can be defined similarly. The mapping $f$ of type $' a \Rightarrow ' a$ aexp given as a parameter is lifted canonically on the types $' a$ aexp and $' a$ bexp, respectively. 

primrec substa :: $( ^ { \prime } a \Rightarrow ^ { \prime } b \ a e x p ) \Rightarrow ^ { \prime } a \ a e x p \Rightarrow ^ { \prime } b$ aexp 

and substb :: $' a \Rightarrow ' b \ a e x p ) \Rightarrow ' a \ b e x p \Rightarrow ' b$ bexp 

# where

substa $f$ $( I F \ b \ a 1 \ a 2 ) = I F$ (substb f b) (substa f a1) (substa f a2) 

| substa $f$ (Sum a1 a2) = Sum (substa f a1) (substa f a2) 

substa $f$ (Diff a1 a2) = Diff (substa f a1) (substa f a2) 

substa $f$ $( V a r \ v ) = f \ v$ 

substa $f$ (Num n) = Num n 

substb $f$ (Less a1 a2) = Less (substa f a1) (substa f a2) 

substb $f$ (And b1 b2) = And (substb f b1) (substb f b2) 

substb $f$ (Neg b) = Neg (substb f b) 

In textbooks about semantics one often finds substitution theorems, which express the relationship between substitution and evaluation. For $' a$ aexp and $' a$ bexp, we can prove such a theorem by mutual induction, followed by simplification. 

# lemma subst_one:

evala env (substa (Var (v := a 0)) a) = evala (env (v := evala env a 0)) a 

evalb env (substb (Var (v := a 0)) b) = evalb (env (v := evala env a 0)) $b$ 

by (induct a and b) simp_all 

# lemma subst_all:

evala env (substa s a) = evala (λx. evala env (s x)) a 

evalb env (substb s b) = evalb (λx. evala env (s x)) b 

by (induct a and b) simp_all 

# Example: a substitution function for terms

Functions on datatypes with nested recursion are also defined by mutual primitive recursion. 

datatype $( \ l ^ { \prime } a , \ l ^ { \prime } b ) \ t e r m = \ l a r \ l ^ { \prime } a \ \vert \ A p p \ ^ { \prime } b \ ( \ l ^ { \prime } a , \ l ^ { \prime } b )$ term list 

A substitution function on type $( ^ { \prime } a , ~ ^ { \prime } b )$ term can be defined as follows, by working simultaneously on $( ^ { \prime } a , ~ ^ { \prime } b )$ term list: 

primrec subst_term :: $^ { \prime } a \Rightarrow ( ^ { \prime } a , ^ { \prime } b ) \ t e r m ) \Rightarrow ( ^ { \prime } a , ^ { \prime } b ) \ t e r m \Rightarrow ( ^ { \prime } a , ^ { \prime } b )$ $e r m \Rightarrow ( ^ { \prime } a , \ ^ { \prime } b )$ term and subst_term_list :: ( $' a \Rightarrow ( ^ { \prime } a , \ ^ { \prime } b ) \ t e r m ) \Rightarrow ( ^ { \prime } a , \ ^ { \prime } b )$ term $l i s t \Rightarrow ( \mathit { ' a } , \mathit { ' b } )$ term list where 

```txt
subst_term f (Var a) = f a
| subst_term f (App b ts) = App b (subst_term_list f ts)
| subst_term_list f [] = []
| subst_term_list f (t # ts) = subst_term f t # subst_term_list f ts 
```

The recursion scheme follows the structure of the unfolded definition of type $( ^ { \prime } a , ~ ^ { \prime } b )$ term. To prove properties of this substitution function, mutual induction is needed: 

lemma subst_term (subst_term $f1\circ f2$ ） $t =$ subst_term $f1$ (subst_term $f2$ t) and  
subst_term_list (subst_term $f1\circ f2$ ) ts=  
subst_term_list $f1$ (subst_term_list $f2$ ts)  
by (induct t and ts rule: subst_term.induct subst_term_list.induct) simp_all 

# Example: a map function for infinitely branching trees

Defining functions on infinitely branching datatypes by primitive recursion is just as easy. 

datatype 0a tree = Atom $^ \prime a \mid$ Branch nat ⇒ 0a tree 

```txt
primrec map_tree :: ('a => 'b) => 'a tree => 'b tree where map_tree f (Atom a) = Atom (f a) | map_tree f (Branch ts) = Branch (\lambda x. map_tree f (ts x)) 
```

Note that all occurrences of functions such as ts above must be applied to an argument. In particular, map_tree $f \circ t s$ is not allowed here. 

Here is a simple composition lemma for map_tree: 

lemma map_tree g (map_tree f t) = map_tree (g ◦ f ) t 

by (induct t) simp_all 

# 11.2.1 Proof methods related to recursive definitions

pat_completeness : method 

relation : method 

lexicographic_order : method 

size_change : method 

termination_simp : attribute 

induction_schema : method 

relation term 

lexicographic_order 

clasimpmod 

size_change 

orders 

clasimpmod 

induction_schema 

orders 

max 

min 

ms 

pat_completeness is a specialized method to solve goals regarding the completeness of pattern matching, as required by the function package (cf. [25]). 

relation $R$ introduces a termination proof using the relation $R$ . The resulting proof state will contain goals expressing that $R$ is wellfounded, and that the arguments of recursive calls decrease with respect to $R$ . Usually, this method is used as the initial proof step of manual termination proofs. 

lexicographic_order attempts a fully automated termination proof by searching for a lexicographic combination of size measures on the arguments of the function. The method accepts the same arguments as the auto method, which it uses internally to prove local descents. The clasimpmod modifiers are accepted (as for auto). 

In case of failure, extensive information is printed, which can help to analyse the situation (cf. [25]). 

size_change also works on termination goals, using a variation of the sizechange principle, together with a graph decomposition technique (see [26] for details). Three kinds of orders are used internally: max, min, and ms (multiset), which is only available when the theory Multiset is loaded. When no order kinds are given, they are tried in order. The search for a termination proof uses SAT solving internally. 

For local descent proofs, the clasimpmod modifiers are accepted (as for auto). 

termination_simp declares extra rules for the simplifier, when invoked in termination proofs. This can be useful, e.g., for special rules involving size estimations. 

induction_schema derives user-specified induction rules from well-founded induction and completeness of patterns. This factors out some operations that are done internally by the function package and makes them available separately. See ~~/src/HOL/Examples/ Induction_Schema.thy for examples. 

# 11.2.2 Functions with explicit partiality

partial_function : local_theory → local_theory partial_function_mono : attribute 

partial_function (mode) defines recursive functions based on fixpoints in complete partial orders. No termination proof is required from the user or constructed internally. Instead, the possibility of non-termination is modelled explicitly in the result type, which contains an explicit bottom element. 

Pattern matching and mutual recursion are currently not supported. Thus, the specification consists of a single function described by a single recursive equation. 

There are no fixed syntactic restrictions on the body of the function, but the induced functional must be provably monotonic wrt. the underlying order. The monotonicity proof is performed internally, and the definition is rejected when it fails. The proof can be influenced by declaring hints using the partial_function_mono attribute. 

The mandatory mode argument specifies the mode of operation of the command, which directly corresponds to a complete partial order on the result type. By default, the following modes are defined: 

option defines functions that map into the option type. Here, the value None is used to model a non-terminating computation. Monotonicity requires that if None is returned by a recursive call, then the overall result must also be None. This is best achieved through the use of the monadic operator Option.bind. 

tailrec defines functions with an arbitrary result type and uses the slightly degenerated partial order where undefined is the bottom element. Now, monotonicity requires that if undefined is returned by a recursive call, then the overall result must also be undefined. In practice, this is only satisfied when each recursive call is a tail call, whose result is directly returned. Thus, this mode of operation allows the definition of arbitrary tail-recursive functions. 

Experienced users may define new modes by instantiating the locale partial_function_definitions appropriately. 

partial_function_mono declares rules for use in the internal monotonicity proofs of partial function definitions. 

# 11.2.3 Old-style recursive function definitions (TFL)

recdef : theory → theory) 

The old TFL command recdef for defining recursive is mostly obsolete; function or fun should be used instead. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b2d4d0bf103ec1ecb422117a02e6d2ee6ce90cf4ef06a935c40ff8129d696440.jpg)


hints 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ad922c8d7a6724134a7a07c7ef9a0a796211c561e29c4b18450a9b6e605e8fa0.jpg)


recdefmod 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/85e4dd7a33156fad1c8cbfa41904725c21a5a477e99325485a4e41dd3107ecaa.jpg)


recdef defines general well-founded recursive functions (using the TFL package). The “(permissive)” option tells TFL to recover from failed proof attempts, returning unfinished results. The recdef_simp, recdef_cong, and recdef_wf hints refer to auxiliary rules to be used in the internal automated proof process of TFL. Additional clasimpmod declarations may be given to tune the context of the Simplifier (cf. §9.3) and Classical reasoner (cf. §9.4). 

Hints for recdef may be also declared globally, using the following attributes. 

recdef_simp : attribute 

recdef_cong : attribute 

recdef_wf : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/46d8b8a8cf5b9a6abcd624b0151ddf53daf6c606f9348fa9e449c5f32f4e5298.jpg)


# 11.3 Adhoc overloading of constants

adhoc_overloading : local_theory → local_theory 

no_adhoc_overloading : local_theory → local_theory 

show_variants : attribute default false 

Adhoc overloading allows to overload a constant depending on its type. Typically this involves the introduction of an uninterpreted constant (used for input and output) and the addition of some variants (used internally). For examples see ~~/src/HOL/Examples/Adhoc_Overloading_Examples.thy and ~~/src/HOL/Library/Monad_Syntax.thy. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b00f04d338539aee21eab5e56a0004259a179a111d2fdd128fed50c87bef4040.jpg)


adhoc_overloading c $v _ { 1 }$ ... $v _ { n }$ associates variants with an existing constant. 

no_adhoc_overloading is similar to adhoc_overloading, but removes the specified variants from the present context. 

show_variants controls printing of variants of overloaded constants. If enabled, the internally used variants are printed instead of their respective overloaded constants. This is occasionally useful to check whether the system agrees with a user’s expectations about derived variants. 

# 11.4 Definition by specification

specification : theory → proof (prove) 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/35aa76264d90b697348c520a2be2e5207433772b00837c09aeab668a24d40aed.jpg)


decl 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b8acdf0de38880139acb4400922f3d97fb126a5ff011821e3859dfbacef80f0b.jpg)


specification decls $\varphi$ sets up a goal stating the existence of terms with the properties specified to hold for the constants given in decls. After finishing the proof, the theory will be augmented with definitions for the given constants, as well as with theorems stating the properties for these constants. 

decl declares a constant to be defined by the specification given. The definition for the constant $c$ is bound to the name c_def unless a theorem name is given in the declaration. Overloaded constants should be declared as such. 

# 11.5 Old-style datatypes

old_rep_datatype : theory → proof (prove) 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/48617dab161d5c8497dcf31902c2fba7843a56c19cb4dd4dcd79e7d7c2bf5818.jpg)


spec 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d77a704c1e9dd9df8491c520cd52c8e71427a898801c5f26daa5177a607951c5.jpg)


cons 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/abce13e85f5846cdb35cfe5072db8deb502f2d359b149c5f2d2627ff913c74b7.jpg)


old_rep_datatype represents existing types as old-style datatypes. 

These commands are mostly obsolete; datatype should be used instead. 

See [8] for more details on datatypes. Apart from proper proof methods for case analysis and induction, there are also emulations of ML tactics case_tac and induct_tac available, see §12.9; these admit to refer directly to the internal structure of subgoals (including internally bound parameters). 

# Examples

We define a type of finite sequences, with slightly different names than the existing $' a$ list that is already in Main: 

datatype 0a seq = Empty | Seq 0a 0a seq 

We can now prove some simple lemma by structural induction: 

lemma Seq x xs 6= xs 

proof (induct xs arbitrary: x) 

case Empty 

This case can be proved using the simplifier: the freeness properties of the datatype are already declared as simp rules. 

show Seq x Empty 6= Empty 

```txt
bysimp next case (Seq y ys) 
```

The step case is proved similarly. 

show Seq $x$ (Seq $y$ ys) $\neq$ Seq $y$ ys using $\langle \text{Seq} y$ ys $\neq$ ys> by simp qed 

Here is a more succinct version of the same proof: 

lemma Seq $x$ xs $\neq$ xs by (induct xs arbitrary: x) simp_all 

# 11.6 Records

In principle, records merely generalize the concept of tuples, where components may be addressed by labels instead of just position. The logical infrastructure of records in Isabelle/HOL is slightly more advanced, though, supporting truly extensible record schemes. This admits operations that are polymorphic with respect to record extension, yielding “object-oriented” effects like (single) inheritance. See also [35] for more details on object-oriented verification and record subtyping in HOL. 

# 11.6.1 Basic concepts

Isabelle/HOL supports both fixed and schematic records at the level of terms and types. The notation is as follows: 

<table><tr><td></td><td>record terms</td><td>record types</td></tr><tr><td>fixed</td><td>(|x = a, y = b|)</td><td>(|x :: A, y :: B|)</td></tr><tr><td>schematic</td><td>(|x = a, y = b, ... = m|)</td><td>(|x :: A, y :: B, ... :: M|)</td></tr></table>

The ASCII representation of $\Vert x = a \Vert$ is $\left( \mid x = a \mid \right.$ ). 

A fixed record $\left( \left| x = a \right. \right.$ , $y = b$ |) has field $x$ of value $a$ and field $y$ of value $b$ . The corresponding type is $( \ v { x } : \ v { x } 4 , \ v { y } : : \ v { B } )$ , assuming that $a : : A$ and $b : : B$ . A record scheme like $\ ( x = a$ , $y = b$ , . . . = m|) contains fields $x$ and $y$ as before, but also possibly further fields as indicated by the “. . . ” notation (which is actually part of the syntax). The improper field “. . . ” of a record scheme is called the more part. Logically it is just a free variable, which is occasionally referred to as “row variable” in the literature. The more part 

of a record scheme may be instantiated by zero or more further components. For example, the previous scheme may get instantiated to $\left( \left| x = a \right. \right.$ , $y = b$ , $z$ $\mathbf { \Sigma } = c , \dots = m ^ { \prime } $ , where $m ^ { \prime }$ refers to a different more part. Fixed records are special instances of record schemes, where “. . . ” is properly terminated by the () :: unit element. In fact, $\textstyle \left\| x = a , y = b \right\|$ is just an abbreviation for (|x = a, y = b, . . . = ()|). 

Two key observations make extensible records in a simply typed language like HOL work out: 

1. the more part is internalized, as a free term or type variable, 

2. field names are externalized, they cannot be accessed within the logic as first-class values. 

In Isabelle/HOL record types have to be defined explicitly, fixing their field names and types, and their (optional) parent record. Afterwards, records may be formed using above syntax, while obeying the canonical order of fields as given by their declaration. The record package provides several standard operations like selectors and updates. The common setup for various generic proof tools enable succinct reasoning patterns. See also the Isabelle/HOL tutorial [38] for further instructions on using records in practice. 

# 11.6.2 Record specifications

record : theory → theory 

print_record : context → 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/49a195173105e0ae9ace67683366ad5f5f0a3a9305438fefca6220affe657601.jpg)


# constdecl

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/429cc81e63531e66292394172377929b0206c5247c7e8f3df722f8bc1e7202ef.jpg)


# modes

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/9eadd1979ad7c028d0fa12d0991cc1ef1c00aee419fa143584b1302558cd288f.jpg)


record $\left( \alpha _ { 1 } , \ldots , \alpha _ { m } \right)$ $t = \tau + c _ { 1 } : : \sigma _ { 1 } \ldots c _ { n } : : \sigma _ { n }$ $c _ { n } : : \sigma _ { n }$ defines extensible record type $( \alpha _ { 1 } , \ldots , \alpha _ { m } ) \ \cdot$ t, derived from the optional parent record $\tau$ by adding new field components $c _ { i } : \because \sigma _ { i }$ etc. 

The type variables of $\tau$ and $\sigma _ { i }$ need to be covered by the (distinct) parameters $\alpha _ { 1 }$ , . . . , $\alpha _ { m }$ . Type constructor $t$ has to be new, while $\tau$ needs to specify an instance of an existing record type. At least one new field $c _ { i }$ has to be specified. Basically, field names need to belong to a unique record. This is not a real restriction in practice, since fields are qualified by the record name internally. 

The parent record specification $\tau$ is optional; if omitted $t$ becomes a root record. The hierarchy of all records declared within a theory context forms a forest structure, i.e. a set of trees starting with a root record each. There is no way to merge multiple parent records! 

For convenience, $( \alpha _ { 1 } , \ldots , \alpha _ { m } )$ $t$ is made a type abbreviation for the fixed record type $( \left. { c _ { 1 } : \sigma _ { 1 } } , \ . \ . . , \ c _ { n } : : \sigma _ { n } \right.$ , likewise is $( \alpha _ { 1 } , \ldots , \alpha _ { m } , \zeta )$ t_scheme made an abbreviation for (|c1 :: σ1, . . . , cn :: σn , . . . :: ζ |). 

print_record $\left( \alpha _ { 1 } , \ldots , \alpha _ { m } \right)$ $t$ prints the definition of record $\left( \alpha _ { 1 } , \ldots , \alpha _ { m } \right) t$ . Optionally modes can be specified, which are appended to the current print mode; see §8.1.3. 

# 11.6.3 Record operations

Any record definition of the form presented above produces certain standard operations. Selectors and updates are provided for any field, including the improper one “more”. There are also cumulative record constructor functions. To simplify the presentation below, we assume for now that $( \alpha _ { 1 } , \ldots , \alpha _ { m } )$ $t$ is a root record with fields $c _ { 1 } : : \sigma _ { 1 }$ , . . . , $c _ { n } : : \sigma _ { n }$ . 

Selectors and updates are available for any field (including “more”): 

$$
\begin{array}{l} c _ {i} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \vdots (\left\lceil \bar {c} :: \bar {\sigma}, \dots :: \zeta \right\rceil) \Rightarrow \sigma_ {i} \\ c _ {i \_} \text {u p d a t e}: (\sigma_ {i} \Rightarrow \sigma_ {i}) \Rightarrow (\left| \bar {c}: \bar {\sigma}, \dots : \zeta \right|) \Rightarrow (\left| \bar {c}: \bar {\sigma}, \dots : \zeta \right|) \\ \end{array}
$$

There is special syntax for application of updates: $r ( \| x : = a \|$ abbreviates term $x$ _update $( \lambda \_ a )$ r. Further notation for repeated updates is also available: $r ( \| x : = a \| ) ( y : = b \| ) ( z : = c \|$ may be written $r ( | x : = a$ , $y : = b$ , $z : = c$ |). Note that because of postfix notation the order of fields shown here is reverse than in the actual term. Since repeated updates are just function applications, fields may be freely permuted in $\scriptstyle ( | x : = a$ , $y : = b$ , z := c|), as far as logical equality is concerned. Thus commutativity of independent updates can be proven within the logic for any two fields, but not as a general theorem. 

The make operation provides a cumulative record constructor function: 

$$
t. m a k e \quad :: \quad \sigma_ {1} \Rightarrow \dots \sigma_ {n} \Rightarrow (\left| \overline {{c}}:: \overline {{\sigma}} \right|)
$$

We now reconsider the case of non-root records, which are derived of some parent. In general, the latter may depend on another parent as well, resulting in a list of ancestor records. Appending the lists of fields of all ancestors results in a certain field prefix. The record package automatically takes care of this by lifting operations over this context of ancestor fields. Assuming that $\left( \alpha _ { 1 } , \ldots , \alpha _ { m } \right)$ $t$ has ancestor fields $b _ { 1 } : : \varrho _ { 1 }$ , . . . , $b _ { k } : : \varrho _ { k }$ , the above record operations will get the following types: 

$$
c _ {i} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \left(\left| \bar {b} :: \bar {\varrho}, \bar {c}:: \bar {\sigma}, \dots :: \zeta \right|\right) \Rightarrow \sigma_ {i}
$$

$$
c _ {i \_} u p d a t e: (\sigma_ {i} \Rightarrow \sigma_ {i}) \Rightarrow (| \bar {b}: \bar {\varrho}, \bar {c}: \bar {\sigma}, \dots : \zeta |) \Rightarrow (| \bar {b}: \bar {\varrho}, \bar {c}: \bar {\sigma}, \dots : \zeta |)
$$

$$
t. m a k e \quad \because \quad \varrho_ {1} \Rightarrow \dots \quad \varrho_ {k} \Rightarrow \sigma_ {1} \Rightarrow \dots \quad \sigma_ {n} \Rightarrow (\left\lceil \bar {b}: \bar {\varrho}, \bar {c}: \bar {\sigma} \right\rceil)
$$

Some further operations address the extension aspect of a derived record scheme specifically: t.fields produces a record fragment consisting of exactly 

the new fields introduced here (the result may serve as a more part elsewhere); t.extend takes a fixed record and adds a given more part; t.truncate restricts a record scheme to a fixed record. 

Note that t.make and t.fields coincide for root records. 

# 11.6.4 Derived rules and proof tools

The record package proves several results internally, declaring these facts to appropriate proof tools. This enables users to reason about record structures quite conveniently. Assume that $t$ is a record type as specified above. 

1. Standard conversions for selectors or updates applied to record constructor terms are made part of the default Simplifier context; thus proofs by reduction of basic operations merely require the simp method without further arguments. These rules are available as t.simps, too. 

2. Selectors applied to updated records are automatically reduced by an internal simplification procedure, which is also part of the standard Simplifier setup. 

3. Inject equations of a form analogous to $( x , y ) = ( x ^ { \prime } , y ^ { \prime } ) \equiv x = x ^ { \prime } \wedge y$ $\mathit { \Theta } = y ^ { \prime }$ are declared to the Simplifier and Classical Reasoner as $i f f$ rules. These rules are available as $t . i f f s$ . 

4. The introduction rule for record equality analogous to $\textit { x r } = \textit { x r } ^ { \prime } \Longrightarrow$ $\ d \cdot \ d r = \ d y \ d r ^ { \prime } \dots \Longrightarrow \ d r = \ d r ^ { \prime }$ is declared to the Simplifier, and as the basic rule context as “intro?”. The rule is called t.equality. 

5. Representations of arbitrary record expressions as canonical constructor terms are provided both in cases and induct format (cf. the generic proof methods of the same name, §6.5). Several variations are available, for fixed records, record schemes, more parts etc. 

The generic proof methods are sufficiently smart to pick the most sensible rule according to the type of the indicated record expression: users just need to apply something like “(cases r)” to a certain proof problem. 

6. The derived record operations t.make, t.fields, t.extend, t.truncate are not treated automatically, but usually need to be expanded by hand, using the collective fact t.defs. 

# Examples

See ~~/src/HOL/Examples/Records.thy, for example. 

# 11.7 Semantic subtype definitions

typedef : local_theory → proof (prove) 

A type definition identifies a new type with a non-empty subset of an existing type. More precisely, the new type is defined by exhibiting an existing type $\tau$ , a set $A : \tau$ set, and proving $\exists x$ . $x \in A$ . Thus $A$ is a non-empty subset of $\tau$ , and the new type denotes this subset. New functions are postulated that establish an isomorphism between the new type and the subset. In general, the type $\tau$ may involve type variables $\alpha _ { 1 }$ , . . . , $\alpha _ { n }$ which means that the type definition produces a type constructor $\left( \alpha _ { 1 } , \ldots , \alpha _ { n } \right)$ $t$ depending on those type arguments. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/6dadddfff401ab9632687f6130b5cc94e42de950d557acc4b15a247e4fdc3147.jpg)


overloaded 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/aeadd65ea6b363258a19ec5c6773ef4927d5f548afe3e5a1690092af7265aae5.jpg)


abs_type 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/745201ecacf36edd2da4bdbb2acdd1b207a69246231580f3fa4cb4782b794b5d.jpg)


rep_set 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7c4b6b4574ae59689c10159e313ce409354e7c686b5def5ba59e705e4a680e3b.jpg)


To understand the concept of type definition better, we need to recount its somewhat complex history. The HOL logic goes back to the “Simple Theory of Types” (STT) of A. Church [14], which is further explained in the book by P. Andrews [1]. The overview article by W. Farmer [16] points out the “seven virtues” of this relatively simple family of logics. STT has only ground types, without polymorphism and without type definitions. 

M. Gordon [19] augmented Church’s STT by adding schematic polymorphism (type variables and type constructors) and a facility to introduce new types as semantic subtypes from existing types. This genuine extension of the logic was explained semantically by A. Pitts in the book of the original Cambridge HOL88 system [50]. Type definitions work in this setting, because the general model-theory of STT is restricted to models that ensure that the universe of type interpretations is closed by forming subsets (via predicates taken from the logic). 

Isabelle/HOL goes beyond Gordon-style HOL by admitting overloaded constant definitions [57, 23], which are actually a concept of Isabelle/Pure and do not depend on particular set-theoretic semantics of HOL. Over many years, there was no formal checking of semantic type definitions in Isabelle/HOL versus syntactic constant definitions in Isabelle/Pure. So the typedef command was described as “axiomatic” in the sense of §5.5, only with some local checks of the given type and its representing set. 

Recent clarification of overloading in the HOL logic proper [28] demonstrates how the dissimilar concepts of constant definitions versus type definitions may be understood uniformly. This requires an interpretation of Isabelle/HOL that substantially reforms the set-theoretic model of A. Pitts [50], by taking a schematic view on polymorphism and interpreting only ground types in the set-theoretic sense of HOL88. Moreover, typeconstructors may be explicitly overloaded, e.g. by making the subset depend on type-class parameters (cf. §5.8). This is semantically like a dependent type: the meaning relies on the operations provided by different type-class instances. 

typedef (α1, . . . , αn) $t = A$ defines a new type (α1, . . . , αn) $t$ from the set $A$ over an existing type. The set $A$ may contain type variables $\alpha _ { 1 }$ , . . . , 

$\alpha _ { n }$ as specified on the LHS, but no term variables. Non-emptiness of $A$ needs to be proven on the spot, in order to turn the internal conditional characterization into usable theorems. 

The “(overloaded)” option allows the typedef specification to depend on constants that are not (yet) specified and thus left open as parameters, e.g. type-class parameters. 

Within a local theory specification, the newly introduced type constructor cannot depend on parameters or assumptions of the context: this is syntactically impossible in HOL. The non-emptiness proof may formally depend on local assumptions, but this has little practical relevance. 

For typedef $t = A$ the newly introduced type $t$ is accompanied by a pair of morphisms to relate it to the representing set over the old type. By default, the injection from type to set is called Rep_ $t$ and its inverse $A b s \_ t$ : An explicit morphisms specification allows to provide alternative names. 

The logical characterization of typedef uses the predicate of locale type_definition that is defined in Isabelle/HOL. Various basic consequences of that are instantiated accordingly, re-using the locale facts with names derived from the new type constructor. Thus the generic theorem type_definition.Rep is turned into the specific Rep_ $t$ , for example. 

Theorems type_definition.Rep, type_definition.Rep_inverse, and type_definition.Abs_inverse provide the most basic characterization as a corresponding injection/surjection pair (in both directions). The derived rules type_definition.Rep_inject and type_definition.Abs_inject provide a more convenient version of injectivity, suitable for automated proof tools (e.g. in declarations involving simp or iff ). Furthermore, the rules type_definition.Rep_cases / type_definition.Rep_induct, and type_definition.Abs_cases / type_definition.Abs_induct provide alternative views on surjectivity. These rules are already declared as set or type rules for the generic cases and induct methods, respectively. 

# Examples

The following trivial example pulls a three-element type into existence within the formal logical environment of Isabelle/HOL. 

typedef $t h r e e = \{ ( T r u e , T r u e )$ , (True, False), (False, True)} 

by blast 

definition One = Abs_three (True, True) 

definition Two = Abs_three (True, False) 

definition Three = Abs_three (False, True) 

lemma three_distinct: One 6= Two One 6= Three Two 6= Three 

by (simp_all add: One_def Two_def Three_def Abs_three_inject) 

lemma three_cases: 

fixes x :: three obtains $x = O n e \mid x = T w o \mid x = T h r e e$ 

by (cases x) (auto simp: One_def Two_def Three_def Abs_three_inject) 

Note that such trivial constructions are better done with derived specification mechanisms such as datatype: 

datatype three = One | Two | Three 

This avoids re-doing basic definitions and proofs from the primitive typedef above. 

# 11.8 Functorial structure of types

functor : local_theory → proof (prove) 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/44fefe7e8d30c174a083d3907fc0b8f6900748c6c0d5e258c3e82713bb2b4498.jpg)


functor prefix: $m$ allows to prove and register properties about the functorial structure of type constructors. These properties then can be used by other packages to deal with those type constructors in certain type constructions. Characteristic theorems are noted in the current local theory. By default, they are prefixed with the base name of the type constructor, an explicit prefix can be given alternatively. 

The given term $m$ is considered as mapper for the corresponding type constructor and must conform to the following type pattern: 

$$
m \quad \because \quad \sigma_ {1} \Rightarrow \dots \sigma_ {k} \Rightarrow (\overline {{\alpha}} _ {n}) t \Rightarrow (\overline {{\beta}} _ {n}) t
$$

where $t$ is the type constructor, $\overline { { \alpha } } _ { n }$ and $\beta _ { n }$ are distinct type variables free in the local theory and $\sigma _ { 1 }$ , . . . , $\sigma _ { k }$ is a subsequence of $\alpha _ { 1 } \Rightarrow \beta _ { 1 }$ , $\beta _ { 1 } \Rightarrow \alpha _ { 1 }$ , . . . , $\alpha _ { n } \Rightarrow \beta _ { n }$ , $\beta _ { n } \Rightarrow \alpha _ { n }$ . 

# 11.9 Quotient types with lifting and transfer

The quotient package defines a new quotient type given a raw type and a partial equivalence relation (§11.9.1). The package also historically includes automation for transporting definitions and theorems (§11.9.4), but most of this automation was superseded by the Lifting (§11.9.2) and Transfer (§11.9.3) packages. 

# 11.9.1 Quotient type definition

quotient_type : local_theory → proof (prove) 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c1446c0f53f37f4da11abfa37e333a388f9a585a8a256e816cdcfb31b6f1e095.jpg)


quot_type 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/48b2961b74b77086b4710d6a5f4d464e34fc77c1b60dfff3182c4c2913e2bacd.jpg)


quot_morphisms 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c4175ae9915174643c97d9ee86ef7f2cecbdbbc3419bf2bbc9c42cb82658cd78.jpg)


quot_parametric 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/326a1d33ec252213e1833f4e6e8b1024487ee23949d33236edea22f12e367c1f.jpg)


quotient_type defines a new quotient type $\tau$ . The injection from a quotient type to a raw type is called rep_ $\tau$ , its inverse abs_ $\tau$ unless explicit morphisms specification provides alternative names. quotient_type requires the user to prove that the relation is an equivalence relation (predicate equivp), unless the user specifies explicitly partial in which case the obligation is part_equivp. A quotient defined with partial is weaker in the sense that less things can be proved automatically. 

The command internally proves a Quotient theorem and sets up the Lifting package by the command setup_lifting. Thus the Lifting and Transfer packages can be used also with quotient types defined by quotient_type without any extra set-up. The parametricity theorem for the equivalence relation R can be provided as an extra argument of the command and is passed to the corresponding internal call of setup_lifting. This theorem allows the Lifting package to generate a stronger transfer rule for equality. 

# 11.9.2 Lifting package

The Lifting package allows users to lift terms of the raw type to the abstract type, which is a necessary step in building a library for an abstract type. Lifting defines a new constant by combining coercion functions ( $A b s$ and Rep) with the raw term. It also proves an appropriate transfer rule for the Transfer (§11.9.3) package and, if possible, an equation for the code generator. 

The Lifting package provides two main commands: setup_lifting for initializing the package to work with a new type, and lift_definition for lifting constants. The Lifting package works with all four kinds of type abstraction: type copies, subtypes, total quotients and partial quotients. 

Theoretical background can be found in [24]. 

setup_lifting : local_theory $\rightarrow$ local_theory  
lift_definition : local_theory $\rightarrow$ proof(prove)  
lifting Forget : local_theory $\rightarrow$ local_theory  
lifting_update : local_theory $\rightarrow$ local_theory  
print_quot_maps : context $\rightarrow$ print_quotients : context $\rightarrow$ quot_map : attribute  
relator_eq_onp : attribute  
relatormono : attribute  
relator_distr : attribute  
quot_del : attribute  
liftingrestore : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/afb407704e69a43d5190ccf2449c9dee0348e31b2ce6b7ede30b283f8e779cb3.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0b0d6487d6afed2c92b00b24415d11bcf30674833f0f4527f9c6631ce2291632.jpg)



setup_lifting Sets up the Lifting package to work with a user-defined type. The command supports two modes.


1. The first one is a low-level mode when the user must provide as a first argument of setup_lifting a quotient theorem Quotient R Abs Rep T. The package configures a transfer rule for equality, a domain transfer rules and sets up the lift_definition command to work with the abstract type. An optional theorem reflp $R$ , which certifies that the equivalence relation R is total, can be provided as a second argument. This allows the package to generate stronger transfer rules. And finally, the parametricity theorem for $R$ can be provided as a third argument. This allows the package to generate a stronger transfer rule for equality. 

Users generally will not prove the Quotient theorem manually for new types, as special commands exist to automate the process. 

2. When a new subtype is defined by typedef, lift_definition can be used in its second mode, where only the type_definition theorem type_definition Rep Abs A is used as an argument of the command. The command internally proves the corresponding Quotient theorem and registers it with setup_lifting using its first mode. 

For quotients, the command quotient_type can be used. The command defines a new quotient type and similarly to the previous case, the corresponding Quotient theorem is proved and registered by setup_lifting. 

The command setup_lifting also sets up the code generator for the new type. Later on, when a new constant is defined by lift_definition, the Lifting package proves and registers a code equation (if there is one) for the new constant. 

lift_definition $f : : \tau$ is $t$ Defines a new function $f$ with an abstract type $\tau$ in terms of a corresponding operation $t$ on a representation type. More formally, if $t \because \sigma$ , then the command builds a term $F$ as a corresponding combination of abstraction and representation functions such that $F : :$ $\sigma \Rightarrow \tau$ and defines $f \equiv F t$ . The term $t$ does not have to be necessarily a constant but it can be any term. 

The command opens a proof and the user must discharge a respectfulness proof obligation. For a type copy, i.e. a typedef with UNIV, the obligation is discharged automatically. The proof goal is presented in a user-friendly, readable form. A respectfulness theorem in the standard format $f$ .rsp and a transfer rule $f$ .transfer for the Transfer package are generated by the package. 

The user can specify a parametricity theorems for $t$ after the keyword parametric, which allows the command to generate parametric transfer rules for $f$ . 

For each constant defined through trivial quotients (type copies or subtypes) $f$ .rep_eq is generated. The equation is a code certificate that defines $f$ using the representation function. 

For each constant $f . a b s \_ e q$ is generated. The equation is unconditional for total quotients. The equation defines $f$ using the abstraction function. 

Integration with [code abstract]: For subtypes (e.g. corresponding to a datatype invariant, such as 0a dlist), lift_definition uses a code certificate theorem $f$ .rep_eq as a code equation. Because of the limitation of the code generator, $f$ $f . r e p \_ e q$ cannot be used as a code equation if the subtype occurs inside the result type rather than at the top level (e.g. function returning $' a$ dlist option vs. 0a dlist). 

In this case, an extension of lift_definition can be invoked by specifying the flag code_dt. This extension enables code execution through series of internal type and lifting definitions if the return type $\tau$ meets the following inductive conditions: 

$\tau$ is a type variable 

$\tau = \tau _ { 1 } \ldots \tau _ { n } \kappa$ , where $\kappa$ is an abstract type constructor and $\tau _ { 1 } \ldots .$ $\tau _ { n }$ do not contain abstract types (i.e. int dlist is allowed whereas int dlist dlist not) 

τ = τ 1 . . . τ n κ, $\kappa$ is a type constructor that was defined as a (co)datatype whose constructor argument types do not contain either nonfree datatypes or the function type. 

Integration with [code equation]: For total quotients, lift_definition uses f .abs_eq as a code equation. 

lifting_forget and lifting_update These two commands serve for storing and deleting the set-up of the Lifting package and corresponding transfer rules defined by this package. This is useful for hiding of type construction details of an abstract type when the construction is finished but it still allows additions to this construction when this is later necessary. 

Whenever the Lifting package is set up with a new abstract type $\tau$ by lift_definition, the package defines a new bundle that is called $^ { \prime }$ .lifting. This bundle already includes set-up for the Lifting package. The new transfer rules introduced by lift_definition can be stored in the bundle by the command lifting_update $^ { \prime }$ .lifting. 

The command lifting_forget $\tau$ .lifting deletes set-up of the Lifting package for $\tau$ and deletes all the transfer rules that were introduced by lift_definition using $\tau$ as an abstract type. 

The stored set-up in a bundle can be reintroduced by the Isar commands for including a bundle (include, includes and including). 

print_quot_maps prints stored quotient map theorems. 

print_quotients prints stored quotient theorems. 

quot_map registers a quotient map theorem, a theorem showing how to “lift” quotients over type constructors. E.g. Quotient R Abs Rep $T \Longrightarrow$ Quotient (rel_set R) (image Abs) (image Rep) (rel_set T ). For examples see ~~/src/HOL/Lifting_Set.thy or ~~/src/HOL/Lifting.thy. This property is proved automatically if the involved type is BNF without dead variables. 

relator_eq_onp registers a theorem that shows that a relator applied to an equality restricted by a predicate $P$ (i.e. eq_onp $P$ ) is equal to a predicator applied to the $P$ . The combinator eq_onp is used for internal encoding of proper subtypes. Such theorems allows the package to hide eq_onp from a user in a user-readable form of a respectfulness theorem. For examples see ~~/src/HOL/Lifting_Set.thy or $\sim \sim /$ src/HOL/Lifting.thy. This property is proved automatically if the involved type is BNF without dead variables. 

relator_mono registers a property describing a monotonicity of a relator. E.g. $A \leq B \Longrightarrow$ rel_set A ≤ rel_set B. This property is needed for proving a stronger transfer rule in lift_definition when a parametricity theorem for the raw term is specified and also for the reflexivity prover. For examples see ~~/src/HOL/Lifting_Set.thy or $\sim / \tt s r c /$ HOL/Lifting.thy. This property is proved automatically if the involved type is BNF without dead variables. 

relator_distr registers a property describing a distributivity of the relation composition and a relator. E.g. rel_set R ◦◦ rel_set S = rel_set (R ◦◦ S ). This property is needed for proving a stronger transfer rule in lift_definition when a parametricity theorem for the raw term is specified. When this equality does not hold unconditionally (e.g. for the function type), the user can specified each direction separately and also register multiple theorems with different set of assumptions. This attribute can be used only after the monotonicity property was already registered by relator_mono. For examples see ~~/src/ HOL/Lifting_Set.thy or ~~/src/HOL/Lifting.thy. This property is proved automatically if the involved type is BNF without dead variables. 

quot_del deletes a corresponding Quotient theorem from the Lifting infrastructure and thus de-register the corresponding quotient. This effectively causes that lift_definition will not do any lifting for the 

corresponding type. This attribute is rather used for low-level manipulation with set-up of the Lifting package because lifting_forget is preferred for normal usage. 

lifting_restore Quotient_thm pcr_def pcr_cr_eq_thm registers the Quotient theorem Quotient_thm in the Lifting infrastructure and thus sets up lifting for an abstract type $\tau$ (that is defined by Quotient_thm). Optional theorems pcr_def and pcr_cr_eq_thm can be specified to register the parametrized correspondence relation for $\tau$ . E.g. for $' a$ dlist, pcr_def is pcr_dlist A ≡ list_all2 A ◦◦ cr_dlist and pcr_cr_eq_thm is pcr_dlist $( = ) \ = \ ( = )$ . This attribute is rather used for low-level manipulation with set-up of the Lifting package because using of the bundle $^ { \prime }$ .lifting together with the commands lifting_forget and lifting_update is preferred for normal usage. 

Integration with the BNF package [8]: As already mentioned, the theorems that are registered by the following attributes are proved and registered automatically if the involved type is BNF without dead variables: quot_map, relator_eq_onp, relator_mono, relator_distr. Also the definition of a relator and predicator is provided automatically. Moreover, if the BNF represents a datatype, simplification rules for a predicator are again proved automatically. 

# 11.9.3 Transfer package

```txt
transfer : method  
transfer' : method  
transfer_prover : method  
Transfer.transferred : attribute  
untransferred : attribute  
transfer_start : method  
transfer_prover_start : method  
transfer_step : method  
transfer_end : method  
transfer_prover_end : method  
transfer_rule : attribute  
transfer_domain_rule : attribute  
relator_eq : attribute  
relator_domain : attribute 
```

transfer method replaces the current subgoal with a logically equivalent one that uses different types and constants. The replacement of types and constants is guided by the database of transfer rules. Goals are generalized over all free variables by default; this is necessary for variables whose types change, but can be overridden for specific variables with e.g. transfer fixing: x y z. 

transfer 0 is a variant of transfer that allows replacing a subgoal with one that is logically stronger (rather than equivalent). For example, a subgoal involving equality on a quotient type could be replaced with a subgoal involving equality (instead of the corresponding equivalence relation) on the underlying raw type. 

transfer_prover method assists with proving a transfer rule for a new constant, provided the constant is defined in terms of other constants that already have transfer rules. It should be applied after unfolding the constant definitions. 

transfer_start, transfer_step, transfer_end, transfer_prover_start and transfer_prover_end methods are meant to be used for debugging of transfer and transfer_prover, which we can decompose as follows: transfer = (transfer_start, transfer_step+, transfer_end) and transfer_prover = (transfer_prover_start, transfer_step+, transfer_prover_end). For usage examples see ~~/src/HOL/ex/ Transfer_Debug.thy. 

untransferred proves the same equivalent theorem as transfer internally does. 

Transfer.transferred works in the opposite direction than transfer 0. E.g. given the transfer relation $Z N x n \equiv ( x = i n t n )$ , corresponding transfer rules and the theorem $\forall x : : i n t \in \{ 0 . . \}$ . $x < x + 1$ , the attribute would prove $\forall n { : } n a t$ . $n < n + 1$ . The attribute is still in experimental phase of development. 

transfer_rule attribute maintains a collection of transfer rules, which relate constants at two different types. Typical transfer rules may relate different type instances of the same polymorphic constant, or they may relate an operation on a raw type to a corresponding operation on an abstract type (quotient or subtype). For example: 

((A ===> B) ===> list_all2 A ===> list_all2 B) map map 

$( c r \_ i n t = = = = > c r \_ i n t = = = > c r \_ i n t )$ $\left( \lambda ( x , y ) \left( u , v \right) . \left( x { + } u , y { + } v \right) \right)$ plus 

Lemmas involving predicates on relations can also be registered using the same attribute. For example: 

bi_unique $A \Longrightarrow$ (list_all2 A ===> (=)) distinct distinct 

[[bi_unique A; bi_unique $B \| \Longrightarrow b i$ _unique (rel_prod A B) 

Preservation of predicates on relations (bi_unique, bi_total, right_unique, right_total, left_unique, left_total) with the respect to a relator is proved automatically if the involved type is BNF [8] without dead variables. 

transfer_domain_rule attribute maintains a collection of rules, which specify a domain of a transfer relation by a predicate. E.g. given the transfer relation $Z N ~ x ~ n \equiv ~ ( x = i n t ~ n )$ , one can register the following transfer domain rule: Domainp $Z N = ( \lambda x . \ x \ge 0 )$ ). The rules allow the package to produce more readable transferred goals, e.g. when quantifiers are transferred. 

relator_eq attribute collects identity laws for relators of various type constructors, e.g. rel_set $( = ) \ = \ ( = )$ . The transfer method uses these lemmas to infer transfer rules for non-polymorphic constants on the fly. For examples see ~~/src/HOL/Lifting_Set.thy or $\sim / { \tt s r c } / \tt H O L /$ Lifting.thy. This property is proved automatically if the involved type is BNF without dead variables. 

relator_domain attribute collects rules describing domains of relators by predicators. E.g. Domainp (rel_set T ) = (λA. Ball A (Domainp T )). This allows the package to lift transfer domain rules through type constructors. For examples see ~~/src/HOL/Lifting_Set.thy or $\sim \sim /$ src/HOL/Lifting.thy. This property is proved automatically if the involved type is BNF without dead variables. 

Theoretical background can be found in [24]. 

# 11.9.4 Old-style definitions for quotient types

quotient_definition : local_theory $\rightarrow$ proof(prove)  
print_quotmapsQ3 : context $\rightarrow$ print_quotientsQ3 : context $\rightarrow$ print_quotcons : context $\rightarrow$ lifting : method  
lifting_setup : method  
descending : method  
descending_setup : method  
partiality_descending : method  
partiality_descending_setup : method  
regularize : method  
injection : method  
cleaning : method  
quot_thm : attribute  
quot_lifted : attribute  
quot_respect : attribute  
quot Preserve : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/f35035618c4453ed0f7ece47b3dc212ddd143baef6d75c7c8477e27f454e0ea6.jpg)


lifting_setup 

thms 

quotient_definition defines a constant on the quotient type. 

print_quotmapsQ3 prints quotient map functions. 

print_quotientsQ3 prints quotients. 

print_quotconsts prints quotient constants. 

lifting and lifting_setup methods match the current goal with the given raw theorem to be lifted producing three new subgoals: regularization, injection and cleaning subgoals. lifting tries to apply the heuristics for automatically solving these three subgoals and leaves only the subgoals unsolved by the heuristics to the user as opposed to lifting_setup which leaves the three subgoals unsolved. 

descending and descending_setup try to guess a raw statement that would lift to the current subgoal. Such statement is assumed as a new subgoal and descending continues in the same way as lifting does. descending tries to solve the arising regularization, injection and cleaning subgoals with the analogous method descending_setup which leaves the four unsolved subgoals. 

partiality_descending finds the regularized theorem that would lift to the current subgoal, lifts it and leaves as a subgoal. This method can be used with partial equivalence quotients where the non regularized statements would not be true. partiality_descending_setup leaves the injection and cleaning subgoals unchanged. 

regularize applies the regularization heuristics to the current subgoal. 

injection applies the injection heuristics to the current goal using the stored quotient respectfulness theorems. 

cleaning applies the injection cleaning heuristics to the current subgoal using the stored quotient preservation theorems. 

quot_lifted attribute tries to automatically transport the theorem to the quotient type. The attribute uses all the defined quotients types and quotient constants often producing undesired results or theorems that cannot be lifted. 

quot_respect and quot_preserve attributes declare a theorem as a respectfulness and preservation theorem respectively. These are stored in the local theory store and used by the injection and cleaning methods respectively. 

quot_thm declares that a certain theorem is a quotient extension theorem. Quotient extension theorems allow for quotienting inside container types. Given a polymorphic type that serves as a container, a map function defined for this container using functor and a relation map defined for for the container type, the quotient extension theorem should be Quotient3 R Abs Rep =⇒ Quotient3 (rel_map R) (map Abs) (map Rep). Quotient extension theorems are stored in a database and are used all the steps of lifting theorems. 

# Proof tools

# 12.1 Proving propositions

In addition to the standard proof methods, a number of diagnosis tools search for proofs and provide an Isar proof snippet on success. These tools are available via the following commands. 

solve_direct∗ : proof → 

try∗ : proof → 

try0∗ : proof → 

sledgehammer∗ : proof → 

sledgehammer_params : theory → theory 

try 

simp 

intro 

elim 

dest 

thms 

nat 

sledgehammer 

args 

] 

facts 

nat 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/57dc3bf8192db0839713d4285c86e0b1f21c1e88cee48522e4419a962f14a1d4.jpg)


solve_direct checks whether the current subgoals can be solved directly by an existing theorem. Duplicate lemmas can be detected in this way. 

try0 attempts to prove a subgoal using a combination of standard proof methods (auto, simp, blast, etc.). Additional facts supplied via simp:, intro:, elim:, and dest: are passed to the appropriate proof methods. 

try attempts to prove or disprove a subgoal using a combination of provers and disprovers (solve_direct, quickcheck, try0, sledgehammer, nitpick). 

sledgehammer attempts to prove a subgoal using external automatic provers (resolution provers and SMT solvers). See the Sledgehammer manual [9] for details. 

sledgehammer_params changes sledgehammer configuration options persistently. 

# 12.2 Checking and refuting propositions

Identifying incorrect propositions usually involves evaluation of particular assignments and systematic counterexample search. This is supported by the following commands. 

value∗ : context → 

values∗ : context → 

quickcheck∗ : proof → 

nitpick∗ : proof → 

quickcheck_params : theory theory 

nitpick_params : theory theory 

quickcheck_generator : theory theory 

find_unused_assms : context → 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/dbb6620bbfb69d3ff4632ac9553018757257124eadb737210c316fd32554ba40.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d2b994a377f8eabcff2235de052b083739b036d0d1b71e820eff3c05dd3ec5eb.jpg)


quickcheck 

nitpick 

args 

nat 

quickcheck_params 

nitpick_params 

] 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/aeb64b40c9ef18a80a687d3bf6df2fd01e78f14c8ce3689654f1d22361a07e9f.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/426417dbe01e146311c0ec0e32e52aebd2d72d8c2498bcde6a27fb6b3e957345.jpg)


modes 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/2bd32e04311d412a8eefa1c20872875e2fec44732ae665668a6ab6c6672697de.jpg)


args 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c066880139476893c3298f83e1744aac49aeec310f61435e42c25c5127ea90c7.jpg)


value $t$ evaluates and prints a term; optionally modes can be specified, which are appended to the current print mode; see §8.1.3. Evaluation is tried first using ML, falling back to normalization by evaluation if this fails. Alternatively a specific evaluator can be selected using square brackets; typical evaluators use the current set of code equations to normalize and include simp for fully symbolic evaluation using the simplifier, nbe for normalization by evaluation and code for code generation in SML. 

values $t$ enumerates a set comprehension by evaluation and prints its values up to the given number of solutions; optionally modes can be specified, which are appended to the current print mode; see §8.1.3. 

quickcheck tests the current goal for counterexamples using a series of assignments for its free variables; by default the first subgoal is tested, an other can be selected explicitly using an optional goal index. Assignments can be chosen exhausting the search space up to a given size, 

or using a fixed number of random assignments in the search space, or exploring the search space symbolically using narrowing. By default, quickcheck uses exhaustive testing. A number of configuration options are supported for quickcheck, notably: 

tester specifies which testing approach to apply. There are three testers, exhaustive, random, and narrowing. An unknown configuration option is treated as an argument to tester, making tester = optional. When multiple testers are given, these are applied in parallel. If no tester is specified, quickcheck uses the testers that are set active, i.e. configurations quickcheck_exhaustive_active, quickcheck_random_active, quickcheck_narrowing_active are set to true. 

size specifies the maximum size of the search space for assignment values. 

genuine_only sets quickcheck only to return genuine counterexample, but not potentially spurious counterexamples due to underspecified functions. 

abort_potential sets quickcheck to abort once it found a potentially spurious counterexample and to not continue to search for a further genuine counterexample. For this option to be effective, the genuine_only option must be set to false. 

eval takes a term or a list of terms and evaluates these terms under the variable assignment found by quickcheck. This option is currently only supported by the default (exhaustive) tester. 

iterations sets how many sets of assignments are generated for each particular size. 

no_assms specifies whether assumptions in structured proofs should be ignored. 

locale specifies how to process conjectures in a locale context, i.e. they can be interpreted or expanded. The option is a whitespaceseparated list of the two words interpret and expand. The list determines the order they are employed. The default setting is to first use interpretations and then test the expanded conjecture. The option is only provided as attribute declaration, but not as parameter to the command. 

timeout sets the time limit in seconds. 

default_type sets the type(s) generally used to instantiate type variables. 

report if set quickcheck reports how many tests fulfilled the preconditions. 

use_subtype if set quickcheck automatically lifts conjectures to registered subtypes if possible, and tests the lifted conjecture. 

quiet if set quickcheck does not output anything while testing. 

verbose if set quickcheck informs about the current size and cardinality while testing. 

expect can be used to check if the user’s expectation was met (no_expectation, no_counterexample, or counterexample). 

These option can be given within square brackets. 

Using the following type classes, the testers generate values and convert them back into Isabelle terms for displaying counterexamples. 

exhaustive The parameters of the type classes exhaustive and full_exhaustive implement the testing. They take a testing function as a parameter, which takes a value of type $' a$ and optionally produces a counterexample, and a size parameter for the test values. In full_exhaustive, the testing function parameter additionally expects a lazy term reconstruction in the type Code_Evaluation.term of the tested value. 

The canonical implementation for exhaustive testers calls the given testing function on all values up to the given size and stops as soon as a counterexample is found. 

random The operation Quickcheck_Random.random of the type class random generates a pseudo-random value of the given size and a lazy term reconstruction of the value in the type Code_Evaluation.term. A pseudo-randomness generator is defined in theory HOL.Random. 

narrowing implements Haskell’s Lazy Smallcheck [51] using the type classes narrowing and partial_term_of. Variables in the current goal are initially represented as symbolic variables. If the execution of the goal tries to evaluate one of them, the test engine replaces it with refinements provided by narrowing. Narrowing views every value as a sum-of-products which is expressed using the operations Quickcheck_Narrowing.cons (embedding a value), Quickcheck_Narrowing.apply (product) and Quickcheck_Narrowing.sum (sum). The refinement should enable further evaluation of the goal. 

For example, narrowing for the list type $' a$ :: narrowing list can be recursively defined as Quickcheck_Narrowing.sum (Quickcheck_Narrowing.cons []) (Quickcheck_Narrowing.apply (Quickcheck_Narrowing.apply (Quickcheck_Narrowing.cons (#)) narrowing) narrowing). If a symbolic variable of type list is evaluated, it is replaced by (i) the empty list [] and (ii) by a non-empty list whose head and tail can then be recursively refined if needed. 

To reconstruct counterexamples, the operation partial_term_of transforms narrowing’s deep representation of terms to the type Code_Evaluation.term. The deep representation models symbolic variables as Quickcheck_Narrowing.Narrowing_variable, which are normally converted to Code_Evaluation.Free, and refined values as Quickcheck_Narrowing.Narrowing_constructor i args, where $i$ :: integer denotes the index in the sum of refinements. In the above example for lists, 0 corresponds to [] and 1 to (#). 

The command code_datatype sets up partial_term_of such that the $i$ -th refinement is interpreted as the $i$ -th constructor, but it does not ensures consistency with narrowing. 

quickcheck_params changes quickcheck configuration options persistently. 

quickcheck_generator creates random and exhaustive value generators for a given type and operations. It generates values by using the operations as if they were constructors of that type. 

nitpick tests the current goal for counterexamples using a reduction to first-order relational logic. See the Nitpick manual [10] for details. 

nitpick_params changes nitpick configuration options persistently. 

find_unused_assms finds potentially superfluous assumptions in theorems using quickcheck. It takes the theory name to be checked for superfluous assumptions as optional argument. If not provided, it checks the current theory. Options to the internal quickcheck invocations can be changed with common configuration declarations. 

# 12.3 Coercive subtyping

coercion : attribute 

coercion_delete : attribute 

coercion_enabled : attribute 

coercion_map : attribute 

coercion_args : attribute 

Coercive subtyping allows the user to omit explicit type conversions, also called coercions. Type inference will add them as necessary when parsing a term. See [53] for details. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/3a6ef9368b48a3396a8c17771dbbf2f5fb6e10285002b685c8e9038e12a5686d.jpg)


coercion_delete term 

coercion_map term 

coercion_args const 

0 

coercion $f$ registers a new coercion function $f : : \sigma _ { 1 } \Rightarrow \sigma _ { 2 }$ where $\sigma _ { 1 }$ and $\sigma _ { 2 }$ are type constructors without arguments. Coercions are composed by the inference algorithm if needed. Note that the type inference algorithm is complete only if the registered coercions form a lattice. 

coercion_delete $f$ deletes a preceding declaration (using coercion) of the function $f : : \sigma _ { 1 } \Rightarrow \sigma _ { 2 }$ as a coercion. 

coercion_map map registers a new map function to lift coercions through type constructors. The function map must conform to the following type pattern 

$$
m a p \quad : \quad f _ {1} \Rightarrow \dots \Rightarrow f _ {n} \Rightarrow (\alpha_ {1}, \dots , \alpha_ {n}) t \Rightarrow (\beta_ {1}, \dots , \beta_ {n}) t
$$

where $t$ is a type constructor and $f _ { i }$ is of type $\alpha _ { i } \Rightarrow \beta _ { i }$ or $\beta _ { i } \Rightarrow \alpha _ { i }$ . Registering a map function overwrites any existing map function for this particular type constructor. 

coercion_args can be used to disallow coercions to be inserted in certain positions in a term. For example, given the constant $c : \sigma _ { 1 } \Rightarrow \sigma _ { 2 }$ $\Rightarrow \sigma _ { 3 } \Rightarrow \sigma _ { 4 }$ and the list of policies $- ~ + ~ 0$ as arguments, coercions will not be inserted in the first argument of $c$ (policy $-$ ); they may be inserted in the second argument (policy $^ +$ ) even if the constant $c$ itself is in a position where coercions are disallowed; the third argument inherits the allowance of coercsion insertion from the position of the constant $c$ (policy 0). The standard usage of policies is the definition of syntatic constructs (usually extralogical, i.e., processed and stripped during type inference), that should not be destroyed by the insertion of coercions (see, for example, the setup for the case syntax in HOL.Ctr_Sugar). 

coercion_enabled enables the coercion inference algorithm. 

# 12.4 Arithmetic proof support

arith : method arith : attribute linarith_split : attribute 

arith decides linear arithmetic problems (on types nat, int, real). Any current facts are inserted into the goal before running the procedure. 

arith declares facts that are supplied to the arithmetic provers implicitly. 

linarith_split attribute declares case split rules to be expanded before arith is invoked. 

Note that a simpler (but faster) arithmetic prover is already invoked by the Simplifier. 

# 12.5 Intuitionistic proof search

iprover : method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d49ddfcd759418b447a48dd16baf6bf1f967126cba2cbb99ebdf04d061ea2ae9.jpg)


iprover performs intuitionistic proof search, depending on specifically declared rules from the context, or given as explicit arguments. Chained facts are inserted into the goal before commencing proof search. 

Rules need to be classified as intro, elim, or dest; here the “!” indicator refers to “safe” rules, which may be applied aggressively (without considering back-tracking later). Rules declared with “?” are ignored in proof search (the single-step rule method still observes these). An explicit weight annotation may be given as well; otherwise the number of rule premises will be taken into account here. 

# 12.6 Model Elimination and Resolution

meson : method 

metis : method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/3f2d59509d6860ab04e621a36e0c8ae9d72322f285115be7be6c54af58304439.jpg)


meson implements Loveland’s model elimination procedure [30]. See ~~/ src/HOL/ex/Meson_Test.thy for examples. 

metis combines ordered resolution and ordered paramodulation to find firstorder (or mildly higher-order) proofs. The first optional argument specifies a type encoding; see the Sledgehammer manual [9] for details. The directory ~~/src/HOL/Metis_Examples contains several small theories developed to a large extent using metis. 

# 12.7 Algebraic reasoning via Gröbner bases

algebra : method 

algebra : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/1d94da2da4c12d92309a2403ef040db910a3f5e9a7177467a74bbd1c3f05e4f5.jpg)


algebra performs algebraic reasoning via Gröbner bases, see also [13] and [12, §3.2]. The method handles deals with two main classes of problems: 

1. Universal problems over multivariate polynomials in a (semi)- ring/field/idom; the capabilities of the method are augmented according to properties of these structures. For this problem class the method is only complete for algebraically closed fields, since the underlying method is based on Hilbert’s Nullstellensatz, where the equivalence only holds for algebraically closed fields. 

The problems can contain equations $p = 0$ or inequations $q \ne 0$ anywhere within a universal problem statement. 

2. All-exists problems of the following restricted (but useful) form: 

$$
\begin{array}{l} \forall x _ {1} \dots x _ {n}. \\ e _ {1} \left(x _ {1}, \dots , x _ {n}\right) = 0 \wedge \dots \wedge e _ {m} \left(x _ {1}, \dots , x _ {n}\right) = 0 \longrightarrow \\ \left(\exists y _ {1} \dots y _ {k}\right). \\ p _ {1 1} \left(x _ {1}, \dots , x _ {n}\right) * y _ {1} + \dots + p _ {1 k} \left(x _ {1}, \dots , x _ {n}\right) * y _ {k} = 0 \wedge \\ \ldots \wedge \\ p _ {t 1} \left(x _ {1}, \dots , x _ {n}\right) * y _ {1} + \dots + p _ {t k} \left(x _ {1}, \dots , x _ {n}\right) * y _ {k} = 0) \\ \end{array}
$$

Here $e _ { 1 }$ , . . . , $e _ { n }$ and the $p _ { i j }$ are multivariate polynomials only in the variables mentioned as arguments. 

The proof method is preceded by a simplification step, which may be modified by using the form (algebra add: ths1 del: ths2). This acts like declarations for the Simplifier (§9.3) on a private simpset for this tool. 

algebra (as attribute) manages the default collection of pre-simplification rules of the above proof method. 

# Example

The subsequent example is from geometry: collinearity is invariant by rotation. 

type_synonym $p o i n t = i n t \times i n t$ 

fun collinear :: point ⇒ point ⇒ point ⇒ bool where 

collinear $( A x , A y ) \ ( B x , B y ) \ ( C x , C y ) \longleftrightarrow$ 

$$
(A x - B x) * (B y - C y) = (A y - B y) * (B x - C x)
$$

lemma collinear_inv_rotation: 

assumes collinear (Ax, Ay) (Bx, By) (Cx, Cy) and $c ^ { 2 } + s ^ { 2 } = 1$ 

shows collinear $A x * c - A y * s$ , $A y * c + A x * s ,$ 

$$
\left(B x * c - B y * s, B y * c + B x * s\right) \left(C x * c - C y * s, C y * c + C x * s\right)
$$

using assms by (algebra add: collinear.simps) 

See also ~~/src/HOL/Examples/Groebner_Examples.thy. 

# 12.8 Coherent Logic

coherent : method 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/30ca7517580664708c7fa5dfe4fd6344e6d3458a559ee7880e5ad218165219fe.jpg)


coherent solves problems of Coherent Logic [7], which covers applications in confluence theory, lattice theory and projective geometry. See ~~/ src/HOL/Examples/Coherent.thy for some examples. 

# 12.9 Unstructured case analysis and induction

The following tools of Isabelle/HOL support cases analysis and induction in unstructured tactic scripts; see also §6.5 for proper Isar versions of similar ideas. 

case_tac\*: method  
induct_tac\*: method  
ind Cases\*: method  
inductive\_cases\*: local\_theory $\rightarrow$ local\_theory 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d269234e0f111e0620597f91d8de73358dc30fabca2081757a8d9842b51dde89.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/0e7b69afcbc36b584c5d7ba0b87466c223b792e1ee7c46d62d739907f99be3ca.jpg)


rule 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ca9c4258018380b2fed20499112ef802cc6fa2964c44abe1be2b8c46cbf84dfb.jpg)


case_tac and induct_tac admit to reason about inductive types. Rules are selected according to the declarations by the cases and induct attributes, cf. §6.5. The datatype package already takes care of this. 

These unstructured tactics feature both goal addressing and dynamic instantiation. Note that named rule cases are not provided as would be by the proper cases and induct proof methods (see §6.5). Unlike the induct method, induct_tac does not handle structured rule statements, only the compact object-logic conclusion of the subgoal being addressed. 

ind_cases and inductive_cases provide an interface to the internal mk_cases operation. Rules are simplified in an unrestricted forward manner. 

While ind_cases is a proof method to apply the result immediately as elimination rules, inductive_cases provides case split theorems at the theory level for later use. The for argument of the ind_cases method allows to specify a list of variables that should be generalized before applying the resulting rule. 

# 12.10 Adhoc tuples

split_format∗ : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7e1e795c8d173c688eb189f2774ac404aa71b355e9b20c87c4d6797639007501.jpg)


split_format (complete) causes arguments in function applications to be represented canonically according to their tuple type structure. 

Note that this operation tends to invent funny names for new local parameters introduced. 

# Executable code

For validation purposes, it is often useful to execute specifications. In principle, execution could be simulated by Isabelle’s inference kernel, i.e. by a combination of resolution and simplification. Unfortunately, this approach is rather inefficient. A more efficient way of executing specifications is to translate them into a functional programming language such as ML. 

Isabelle provides a generic framework to support code generation from executable specifications. Isabelle/HOL instantiates these mechanisms in a way that is amenable to end-user applications. Code can be generated for functional programs (including overloading using type classes) targeting SML [34], OCaml [29], Haskell [49] and Scala [15]. Conceptually, code generation is split up in three steps: selection of code theorems, translation into an abstract executable view and serialization to a specific target language. Inductive specifications can be executed using the predicate compiler which operates within HOL. See [21] for an introduction. 

export_code* : local_theory $\rightarrow$ local_theory  
code : attribute  
code_datatype : theory $\rightarrow$ theory  
print_codessetup* : context $\rightarrow$ code_unfold : attribute  
code_post : attribute  
code_abbrev : attribute  
print_codeproc* : context $\rightarrow$ code_thms* : context $\rightarrow$ code_deps* : context $\rightarrow$ code_reserved : theory $\rightarrow$ theory  
code_printing : theory $\rightarrow$ theory  
code identitiesifier : theory $\rightarrow$ theory  
code_monad : theory $\rightarrow$ theory  
code_reflect : theory $\rightarrow$ theory  
code_pred : theory $\rightarrow$ proof(prove)  
code_timing : attribute  
code_simp_trace : attribute  
code_routine_trace : attribute 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/bf8941792868e9b67b19628325171af914b36dca3b6423e76e0bb493ec9bb90b.jpg)


export_target 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/b638d24230f9b673bb390ff7373156b6cf244fbcc1c4155901870945475d645d.jpg)


target 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/224d000c381bf675cc5fbefc8249431718256415705d8e772e102cc1576552a7.jpg)


const_expr 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/ecd4935d7a378d7a2eea028402f9dcfb24f46a49f1966f1b712d87a6ffd6ecdb.jpg)


const 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/008d29b9aa4285472e581ac72bdd5daa885af00d9942f854ea89f3d6d4717657.jpg)


type_constructor 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a391831632d2bce7d90abd73bb334fb589a4c245abfeef69c94fe45a7809255e.jpg)


class 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/28af9d6762f2875cc5015a9c884d2d522f6358a8015f0e26d7e0cff395f86df4.jpg)


path 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/8fa1fc82181356325aba7ee4c822f3da3b9750846d1bf7440db5d6c3b3690d5c.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/20fe856e151d332fda233f0e92a30b6799aa10e14056a61d0ad36a6423f71bbd.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a9a540024a82da20ba218eb930bb896ee664b148758e8cd4b768cb571adf6f9c.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c2207b527170b70943041adadedc5603e3fc295d61fad5f55470bef52849f1a0.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/7e680df4f40bad30b3c5cf37cd2cc4843e76203757a54a5e1f49285b2ae5431d.jpg)


symbol_const 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/62b232e78adda80f1b1b990aa555fba5b2f6f9d0935e402cab0cd983f8368f63.jpg)


symbol_type_constructor 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5a142a3ed6e83e082d7c612f9749d717c9b0082b483e4b3c6f66b1b845cf144f.jpg)


symbol_class 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/65b19e6bb083afac48a12e8996486a33294bf8a7fe842c04167a65193324483f.jpg)


symbol_class_relation 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/41d5db3bfbd9b3f368d405f5e0deba6d17ebe498863c310669dacbdff985f5f7.jpg)


symbol_class_instance 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c70e3134986eda0b5be055eab7e1ae00cea3593fa00e8a0d0a743a4777a78826.jpg)


symbol_module 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/f6eecd72a7607b093eb9ad5d4a78e46cc81fe567e3b0c8fba886be101aceecaa.jpg)


syntax 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d32c8ad5af78dc0be87434561f57d62c16d2ef17995d4a04498e2419e1a12a1b.jpg)


printing_const 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/e78d22954892d45beb4dd22d5b122f577a9e4cb322b292dfd6e0192b64df75b0.jpg)


printing_type_constructor 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/f4f7f4faf4dab1677f2aace56e709c80ae34cd2b725a1db95764392e1d6a7e2d.jpg)


printing_class 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/c0d38a15284322f61893b4b2c557169f4191dac4dcdc14670b217fef589c3fcf.jpg)


printing_class_relation 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/f2937cc8500b84ee8345f26116c1da16569c1c14182bb3eae1e2a67d642d9015.jpg)


printing_class_instance 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/a51126e2056fc800fe3acadb7d2bad92a27b4466b3049b51dc146f789c600280.jpg)


printing_module 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d4e0cc26c0e5e4f64cbe3d2971e8277f8fbb2027bdbb95b3210675781c980397.jpg)


for_symbol 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/13a9ffccb8e1b6a5242e5a4e2250d82b62a1b449cf240a500c8fc8fddf5dcd11.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/fd24f30c0b274fdf100d839ec617620600907c936ec5eaf45fcea604591ef36e.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/5a51731e2328554074945d9e1b74b6e61139532569e933e6d585c398a1011a7f.jpg)


# modedecl

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/d02d0402bed80b27b66a1d055cb0f8a07e2628950385979c23399dff8b018f38.jpg)


# modes

![image](https://cdn-mineru.openxlab.org.cn/result/2026-02-24/7bb7938d-8e7b-4a25-bfea-4bb55d49d81a/681b6c4fd7bff636265c85020a4aa3b2fcccde956ca11418b387bccf177abd68.jpg)


export_code generates code for a given list of constants in the specified target language(s). If no serialization instruction is given, only abstract code is generated internally. 

Constants may be specified by giving them literally, referring to all executable constants within a certain theory by giving name._, or referring to all executable constants currently available by giving _. 

By default, exported identifiers are minimized per module. This can be suppressed by prepending open before the list of constants. 

By default, for each involved theory one corresponding name space module is generated. Alternatively, a module name may be specified after the module_name keyword; then all code is placed in this module. 

Generated code is output as logical files within the theory context, as well as session exports that can be retrieved using isabelle export, or isabelle build with option -e and suitable export_files specifications in the session ROOT entry. All files have a common directory prefix: the long theory name plus “code”. The actual file name is determined by the target language together with an optional file_prefix (the default is “export” with a consecutive number within the current theory). For SML, OCaml and Scala, the file prefix becomes a plain file with extension (e.g. “.ML” for SML). For Haskell the file prefix becomes a directory that is populated with a separate file for each module (with extension “.hs”). 

Serializers take an optional list of arguments in parentheses. 

• For Haskell a module name prefix may be given using the “root:” argument; “string_classes” adds a “deriving (Read, Show)” clause to each appropriate datatype declaration. 

• For Scala, “case_insensitive” avoids name clashes on caseinsensitive file systems. 

code declares code equations for code generation. 

Variant code equation declares a conventional equation as code equation. 

Variants code abstype and code abstract declare abstract datatype certificates or code equations on abstract datatype representations respectively. 

Vanilla code falls back to code equation or code abstract depending on the syntactic shape of the underlying equation. 

Variant code del deselects a code equation for code generation. 

Variant code nbe accepts also non-left-linear equations for normalization by evaluation only. 

Variants code drop: and code abort: take a list of constants as arguments and drop all code equations declared for them. In the case of abort, these constants if needed are implemented by program abort (exception). 

Packages declaring code equations usually provide a reasonable default setup. 

code_datatype specifies a constructor set for a logical type. 

print_codesetup gives an overview on selected code equations and code generator datatypes. 

code_unfold declares (or with option “del” removes) theorems which during preprocessing are applied as rewrite rules to any code equation or evaluation input. 

code_post declares (or with option “del” removes) theorems which are applied as rewrite rules to any result of an evaluation. 

code_abbrev declares (or with option “del” removes) equations which are applied as rewrite rules to any result of an evaluation and symmetrically during preprocessing to any code equation or evaluation input. 

print_codeproc prints the setup of the code generator preprocessor. 

code_thms prints a list of theorems representing the corresponding program containing all given constants after preprocessing. 

code_deps visualizes dependencies of theorems representing the corresponding program containing all given constants after preprocessing. 

code_reserved declares a list of names as reserved for a given target, preventing it to be shadowed by any generated code. 

code_printing associates a series of symbols (constants, type constructors, classes, class relations, instances, module names) with target-specific serializations; omitting a serialization deletes an existing serialization. 

code_monad provides an auxiliary mechanism to generate monadic code for Haskell. 

code_identifier associates a a series of symbols (constants, type constructors, classes, class relations, instances, module names) with targetspecific hints how these symbols shall be named. These hints gain precedence over names for symbols with no hints at all. Conflicting hints are subject to name disambiguation. Warning: It is at the discretion of the user to ensure that name prefixes of identifiers in compound statements like type classes or datatypes are still the same. 

code_reflect without a “file_prefix” argument compiles code into the system runtime environment and modifies the code generator setup that future invocations of system runtime code generation referring to one of the “datatypes” or “functions” entities use these precompiled entities. With a “file_prefix” argument, the corresponding code is generated/exported to the specified file (as for export_code) without modifying the code generator setup. 

code_pred creates code equations for a predicate given a set of introduction rules. Optional mode annotations determine which arguments are supposed to be input or output. If alternative introduction rules are declared, one must prove a corresponding elimination rule. 

code_timing scrapes timing samples from different stages of the code generator. 

code_simp_trace traces the simplifier when it is used with code equations. code_runtime_trace traces ML code generated dynamically for execution. 

# Part IV

# Appendix

# Isabelle/Isar quick reference

# A.1 Proof commands

# A.1.1 Main grammar

main $=$ notepad begin statement\* end theorem name: props if name: props for vars proof theorem name: fixes vars assumes name: props shows name: props proof theorem name: fixes vars assumes name: props obtains (name) vars where props | ... proof   
proof $=$ refinement\* proper\_proof   
refinement $=$ apply method supply name $=$ thms subgoal premises name for vars proof using thms unfolding thms   
proper\_proof $=$ proof method? statement\* qed method? done   
statement $=$ $\{\mathrm{state}m e n t^{*}\}$ next note name $=$ thms let term $=$ term write name (mixfix) fix vars assume name: props if props for vars then? goal   
goal $=$ have name: props if name: props for vars proof show name: props if name: props for vars proof 

# A.1.2 Primitives

fix $x$ augment context by $\bigwedge x.\square$ assume $a\colon A$ augment context by $A\Rightarrow \square$ then indicate forward chaining of facts   
have $a\colon A$ prove local result   
show $a\colon A$ prove local result, refining some goal   
using $a$ indicate use of additional facts   
unfolding $a$ unfold definitional equations   
proof $m_{1}\ldots$ qed $m_2$ indicate proof structure and refinements   
{...} indicate explicit blocks   
next switch proof blocks   
note $a = b$ reconsider and declare facts   
let $p = t$ abbreviate terms by higher-order matching   
write $c(mx)$ declare local mixfix syntax 

# A.1.3 Abbreviations and synonyms

by $m_{1} m_{2} \equiv$ proof $m_{1}$ qed $m_{2}$ .. $\equiv$ by standard. . $\equiv$ by this from $a \equiv$ note $a$ then with $a \equiv$ from $a$ and this from this $\equiv$ then 

# A.1.4 Derived elements

$\begin{array}{rl}\mathrm{also}_0 & \approx \\ \mathrm{also}_{n + 1} & \approx \\ \mathrm{finally} & \approx \end{array}$ note calculation $=$ this note calculation $=$ trans [OF calculation this] also from calculation moreover note calculation $=$ calculation this ultimately assume $a$ .. $A$ assume $a$ .. A define $x$ where $x = t$ fix $x$ assume $x\_ def$ .. $x = t$ consider $x$ where $A\mid \dots$ have thesis if $\bigwedge x.A\Rightarrow$ thesis and... for thesis obtain $x$ where $a$ .. $A$ (proof) consider $x$ where $A$ (proof) fix $x$ assume $a$ .. $A$ case $c$ fix $x$ assume $c$ .. $A$ sorry by cheating 

# A.1.5 Diagnostic commands

typ $\tau$ print type   
term $t$ print term   
prop $\varphi$ print proposition   
thm $a$ print fact   
print_statement $a$ print fact in long statement form 

# A.2 Proof methods

# Single steps (forward-chaining facts)

assumption apply some goal assumption   
this apply current facts   
rule a apply some rule   
standard apply standard rule (default for proof)   
contradiction apply $\neg$ elimination rule (any order)   
cases $t$ case analysis (provides cases)   
induct $x$ proof by induction (provides cases) 

# Repeated steps (inserting facts)

```txt
- no rules  
intro a introduction rules  
intro_classeses class introduction rules  
introlocations locale introduction rules (without body)  
unfoldlocations locale introduction rules (with body)  
elima elimination rules  
unfoldation definitional rewrite rules 
```

# Automated proof tools (inserting facts)

iprover intuitionistic proof search blast, fast Classical Reasoner simp,simp_all Simplifier $(+$ Splitter) auto, force Simplifier $^+$ Classical Reasoner arith Arithmetic procedures 

# A.3 Attributes

# Rules

<table><tr><td>OF a</td><td>rule resolved with facts (skipping “_”)</td></tr><tr><td>of t</td><td>rule instantiated with terms (skipping “_”)</td></tr><tr><td>where x = t</td><td>rule instantiated with terms, by variable name</td></tr><tr><td>symmetric</td><td>resolution with symmetry rule</td></tr><tr><td>THEN b</td><td>resolution with another rule</td></tr><tr><td>rule_format</td><td>result put into standard rule format</td></tr><tr><td>elim_format</td><td>destruct rule turned into elimination rule format</td></tr></table>

# Declarations

<table><tr><td>simp</td><td>Simplifier rule</td></tr><tr><td>intro, elim, dest</td><td>Pure or Classical Reasoner rule</td></tr><tr><td>iff</td><td>Simplifier + Classical Reasoner rule</td></tr><tr><td>split</td><td>case split rule</td></tr><tr><td>trans</td><td>transitivity rule</td></tr><tr><td>sym</td><td>symmetry rule</td></tr></table>

# A.4 Rule declarations and methods

<table><tr><td></td><td>rule</td><td>iprover</td><td>blast fast</td><td>simp simp_all</td><td>auto force</td></tr><tr><td>Pure elim! Pure intro!</td><td>×</td><td>×</td><td></td><td></td><td></td></tr><tr><td>Pure elim Pure intro</td><td>×</td><td>×</td><td></td><td></td><td></td></tr><tr><td>elim! intro!</td><td>×</td><td></td><td>×</td><td></td><td>×</td></tr><tr><td>elim intro</td><td>×</td><td></td><td>×</td><td></td><td>×</td></tr><tr><td>iff</td><td>×</td><td></td><td>×</td><td>×</td><td>×</td></tr><tr><td>iff?</td><td>×</td><td></td><td></td><td></td><td></td></tr><tr><td>elim? intro?</td><td>×</td><td></td><td></td><td></td><td></td></tr><tr><td>simp</td><td></td><td></td><td></td><td>×</td><td>×</td></tr><tr><td>cong</td><td></td><td></td><td></td><td>×</td><td>×</td></tr><tr><td>split</td><td></td><td></td><td></td><td>×</td><td>×</td></tr></table>

# A.5 Proof scripts

# A.5.1 Commands

<table><tr><td>apply m</td><td>apply proof method during backwards refinement</td></tr><tr><td>apply_end m</td><td>apply proof method (as if in terminal position)</td></tr><tr><td>supply a</td><td>supply facts during backwards refinement</td></tr><tr><td>subgoal</td><td>nested proof during backwards refinement</td></tr><tr><td>defer n</td><td>move subgoal to end</td></tr><tr><td>prefer n</td><td>move subgoal to start</td></tr><tr><td>back</td><td>backtrack last command</td></tr><tr><td>done</td><td>complete proof</td></tr></table>

# A.5.2 Methods

<table><tr><td>rule_tac_insts</td><td>resolution (with instantiation)</td></tr><tr><td>erule_tac_insts</td><td>elim-resolution (with instantiation)</td></tr><tr><td>drule_tac_insts</td><td>destruct-resolution (with instantiation)</td></tr><tr><td>frule_tac_insts</td><td>forward-resolution (with instantiation)</td></tr><tr><td>cut_tac_insts</td><td>insert facts (with instantiation)</td></tr><tr><td>thin_tac φ</td><td>delete assumptions</td></tr><tr><td>subgoal_tac φ</td><td>new claims</td></tr><tr><td>rewrite_tac x</td><td>rewrite innermost goal parameters</td></tr><tr><td>rotate_tac n</td><td>rotate assumptions of goal</td></tr><tr><td>tactic_text</td><td>arbitrary ML tactic</td></tr><tr><td>case_tac t</td><td>exhaustion (datatypes)</td></tr><tr><td>induct_tac x</td><td>induction (datatypes)</td></tr><tr><td>ind Cases t</td><td>exhaustion + simplification (inductive predicates)</td></tr></table>

# Predefined Isabelle symbols

Isabelle supports an infinite number of non-ASCII symbols, which are represented in source text as \<name> (where name may be any identifier). It is left to front-end tools how to present these symbols to the user. The collection of predefined standard symbols given below is available by default for Isabelle document output, due to appropriate definitions of \isasymname for each \<name> in the isabellesym.sty file. Most of these symbols are displayed properly in Isabelle/jEdit and LAT X generated from Isabelle. 

Moreover, any single symbol (or ASCII character) may be prefixed by \<^sup> for superscript and \<^sub> for subscript, such as A\<^sup>\<star> for $A ^ { \star }$ and A\<^sub>1 for $A _ { 1 }$ . Sub- and superscripts that span a region of text can be marked up with \<^bsub>. . . \<^esub> and \<^bsup>. . . \<^esup> respectively, but note that there are limitations in the typographic rendering quality of this form. Furthermore, all ASCII characters and most other symbols may be printed in bold by prefixing \<^bold> such as \<^bold>\<alpha> for $\pmb { \alpha }$ . Note that \<^sup>, \<^sub>, \<^bold> cannot be combined. 

Further details of Isabelle document preparation are covered in chapter 4. 

<table><tr><td>\&lt;zero&gt;</td><td>0</td><td>\&lt;one&gt;</td><td>1</td></tr><tr><td>\&lt;two&gt;</td><td>2</td><td>\&lt;three&gt;</td><td>3</td></tr><tr><td>\&lt;four&gt;</td><td>4</td><td>\&lt;five&gt;</td><td>5</td></tr><tr><td>\&lt;six&gt;</td><td>6</td><td>\&lt;seven&gt;</td><td>7</td></tr><tr><td>\&lt;eight&gt;</td><td>8</td><td>\&lt;nine&gt;</td><td>9</td></tr><tr><td>\&lt;A&gt;</td><td>A</td><td>\&lt;B&gt;</td><td>B</td></tr><tr><td>\&lt;C&gt;</td><td>C</td><td>\&lt;D&gt;</td><td>D</td></tr><tr><td>\&lt;E&gt;</td><td>E</td><td>\&lt;F&gt;</td><td>F</td></tr><tr><td>\&lt;G&gt;</td><td>G</td><td>\&lt;H&gt;</td><td>H</td></tr><tr><td>\&lt;I&gt;</td><td>I</td><td>\&lt;J&gt;</td><td>J</td></tr><tr><td>\&lt;K&gt;</td><td>K</td><td>\&lt;L&gt;</td><td>L</td></tr><tr><td>\&lt;M&gt;</td><td>M</td><td>\&lt;N&gt;</td><td>N</td></tr><tr><td>\&lt;O&gt;</td><td>O</td><td>\&lt;P&gt;</td><td>P</td></tr><tr><td>\&lt;Q&gt;</td><td>Q</td><td>\&lt;R&gt;</td><td>R</td></tr></table>

<table><tr><td>\&lt;S&gt;</td><td>S</td><td>\&lt;T&gt;</td><td>T</td></tr><tr><td>\&lt;U&gt;</td><td>U</td><td>\&lt;V&gt;</td><td>V</td></tr><tr><td>\&lt;W&gt;</td><td>W</td><td>\&lt;X&gt;</td><td>X</td></tr><tr><td>\&lt;Y&gt;</td><td>Y</td><td>\&lt;Z&gt;</td><td>Z</td></tr><tr><td>\&lt;a&gt;</td><td>a</td><td>\&lt;b&gt;</td><td>b</td></tr><tr><td>\&lt;c&gt;</td><td>c</td><td>\&lt;d&gt;</td><td>d</td></tr><tr><td>\&lt;e&gt;</td><td>e</td><td>\&lt;f&gt;</td><td>f</td></tr><tr><td>\&lt;g&gt;</td><td>g</td><td>\&lt;h&gt;</td><td>h</td></tr><tr><td>\&lt;i&gt;</td><td>i</td><td>\&lt;j&gt;</td><td>j</td></tr><tr><td>\&lt;k&gt;</td><td>k</td><td>\&lt;l&gt;</td><td>l</td></tr><tr><td>\&lt;m&gt;</td><td>m</td><td>\&lt;n&gt;</td><td>n</td></tr><tr><td>\&lt;o&gt;</td><td>o</td><td>\&lt;p&gt;</td><td>p</td></tr><tr><td>\&lt;q&gt;</td><td>q</td><td>\&lt;r&gt;</td><td>r</td></tr><tr><td>\&lt;s&gt;</td><td>s</td><td>\&lt;t&gt;</td><td>t</td></tr><tr><td>\&lt;u&gt;</td><td>u</td><td>\&lt;v&gt;</td><td>v</td></tr><tr><td>\&lt;w&gt;</td><td>w</td><td>\&lt;x&gt;</td><td>x</td></tr><tr><td>\&lt;y&gt;</td><td>y</td><td>\&lt;z&gt;</td><td>z</td></tr><tr><td>\&lt;AA&gt;</td><td>A</td><td>\&lt;BB&gt;</td><td>B</td></tr><tr><td>\&lt;CC&gt;</td><td>C</td><td>\&lt;DD&gt;</td><td>D</td></tr><tr><td>\&lt;EE&gt;</td><td>E</td><td>\&lt;FF&gt;</td><td>F</td></tr><tr><td>\&lt;GG&gt;</td><td>G</td><td>\&lt;HH&gt;</td><td>H</td></tr><tr><td>\&lt;II&gt;</td><td>I</td><td>\&lt;JJ&gt;</td><td>J</td></tr><tr><td>\&lt;KK&gt;</td><td>K</td><td>\&lt;LL&gt;</td><td>L</td></tr><tr><td>\&lt;MM&gt;</td><td>M</td><td>\&lt;NN&gt;</td><td>M</td></tr><tr><td>\&lt;OO&gt;</td><td>O</td><td>\&lt;PP&gt;</td><td>P</td></tr><tr><td>\&lt;QQ&gt;</td><td>Q</td><td>\&lt;RR&gt;</td><td>R</td></tr><tr><td>\&lt;SS&gt;</td><td>S</td><td>\&lt;TT&gt;</td><td>T</td></tr><tr><td>\&lt;UU&gt;</td><td>U</td><td>\&lt;VV&gt;</td><td>U</td></tr><tr><td>\&lt;WW&gt;</td><td>W</td><td>\&lt;XX&gt;</td><td>X</td></tr><tr><td>\&lt;YY&gt;</td><td>Y</td><td>\&lt;ZZ&gt;</td><td>Z</td></tr><tr><td>\&lt;aa&gt;</td><td>a</td><td>\&lt;bb&gt;</td><td>b</td></tr><tr><td>\&lt;cc&gt;</td><td>c</td><td>\&lt;dd&gt;</td><td>d</td></tr><tr><td>\&lt;ee&gt;</td><td>e</td><td>\&lt;ff&gt;</td><td>f</td></tr><tr><td>\&lt;gg&gt;</td><td>g</td><td>\&lt;hh&gt;</td><td>h</td></tr><tr><td>\&lt;ii&gt;</td><td>i</td><td>\&lt;jj&gt;</td><td>j</td></tr><tr><td>\&lt;kk&gt;</td><td>k</td><td>\&lt;ll&gt;</td><td>l</td></tr><tr><td>\&lt;mm&gt;</td><td>m</td><td>\&lt;nn&gt;</td><td>n</td></tr><tr><td>\&lt;oo&gt;</td><td>o</td><td>\&lt;pp&gt;</td><td>p</td></tr><tr><td>\&lt;qq&gt;</td><td>q</td><td>\&lt;rr&gt;</td><td>r</td></tr><tr><td>\&lt;ss&gt;</td><td>s</td><td>\&lt;tt&gt;</td><td>t</td></tr><tr><td>\&lt;uu&gt;</td><td>u</td><td>\&lt;vv&gt;</td><td>v</td></tr><tr><td>\&lt;ww&gt;</td><td>w</td><td>\&lt;xx&gt;</td><td>r</td></tr></table>

<table><tr><td>\yy&gt;</td><td>η</td><td>\zz&gt;</td><td>3</td></tr><tr><td>\alpha</td><td>\beta</td><td>\gamma</td><td>δ</td></tr><tr><td>\epsilon epsilon&gt;</td><td>ε</td><td>\zeta</td><td>ζ</td></tr><tr><td>\eta</td><td>\theta</td><td>\vartheta</td><td>φ</td></tr><tr><td>\iota</td><td>\kappa</td><td>\chi</td><td>κ</td></tr><tr><td>λ</td><td>μ</td><td>\mu</td><td>μ</td></tr><tr><td>nu</td><td>ξ</td><td>\xi</td><td>ξ</td></tr><tr><td>π</td><td>ρ</td><td>\ρ</td><td>ρ</td></tr><tr><td>σ</td><td>τ</td><td>\tau</td><td>τ</td></tr><tr><td>\upsilon</td><td>φ</td><td>\phi</td><td>φ</td></tr><tr><td>χ</td><td>ψ</td><td>\psi</td><td>ψ</td></tr><tr><td>ω</td><td>Γ</td><td>\Gamma</td><td>Γ</td></tr><tr><td>Δ</td><td>Θ</td><td>\Θ</td><td>Θ</td></tr><tr><td>Λ</td><td>Ξ</td><td>Ξ</td><td>Ξ</td></tr><tr><td>Π</td><td>Σ</td><td>Σ</td><td>Σ</td></tr><tr><td>γ</td><td>Φ</td><td>Φ</td><td>Φ</td></tr><tr><td>Ψ</td><td>Ω</td><td>Ω</td><td>Ω</td></tr><tr><td>A</td><td>B</td><td>B</td><td>B</td></tr><tr><td>C</td><td>D</td><td>D</td><td>D</td></tr><tr><td>E</td><td>F</td><td>F</td><td>F</td></tr><tr><td>G</td><td>H</td><td>H</td><td>H</td></tr><tr><td>I</td><td>J</td><td>J</td><td>J</td></tr><tr><td>K</td><td>L</td><td>L</td><td>L</td></tr><tr><td>M</td><td>N</td><td>N</td><td>N</td></tr><tr><td>O</td><td>P</td><td>P</td><td>P</td></tr><tr><td>Q</td><td>R</td><td>R</td><td>R</td></tr><tr><td>S</td><td>T</td><td>T</td><td>T</td></tr><tr><td>U</td><td>V</td><td>V</td><td>V</td></tr><tr><td>W</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Y</td><td>Z</td><td>Z</td><td>Z</td></tr><tr><td>←</td><td>→</td><td>→</td><td>→</td></tr><tr><td>\longleftarrow</td><td>\longrightarrows</td><td>→</td><td>→</td></tr><tr><td>←—</td><td>\longrightarrows</td><td>→</td><td>→</td></tr><tr><td>\longleftarrow</td><td>\longleftarrow</td><td>→</td><td>→</td></tr><tr><td>\rightleftarrows</td><td>←</td><td>\rightleftarrows</td><td>→</td></tr><tr><td>Leftarrow</td><td>←</td><td>Leftarrow</td><td>→</td></tr><tr><td>Longleftarrow</td><td>←</td><td>Longleftarrow</td><td>→</td></tr><tr><td>Leftarrow</td><td>←</td><td>Longleftarrow</td><td>→</td></tr><tr><td>Longleftarrow</td><td>←</td><td>Longleftarrow</td><td>→</td></tr><tr><td>mapsto</td><td>→</td><td>Longmapsto</td><td>→</td></tr><tr><td>midarrow</td><td>-</td><td>Midarrow</td><td>=</td></tr></table>

\<hookleftarrow> $\leftrightarrow$ \<hookrightarrow> $\leftrightarrow$ \<leftharpoondown> $\rightharpoonup$ \<rightharpoondown> $\rightharpoonup$ \<leftharpoonup> $\rightharpoonup$ \<rightharpoonup> $\rightharpoonup$ \<rightleftharpoons> $\Rightarrow$ \<leadsto> $\rightsquigarrow$ \<downharpoonleft> $\downarrow$ \<downharpoonright> $\downarrow$ \<upharpoonleft> $\uparrow$ \<upharpoonright> $\uparrow$ \<restriction> $\uparrow$ \<Colon> $\because$ \<up> $\uparrow$ \<Up> $\uparrow$ \<down> $\downarrow$ \<Down> $\downarrow$ \<updown> $\updownarrow$ \<Updown> $\updownarrow$ \<langle> $\langle$ \<rangle> $\rangle$ \<llangle> $\langle$ \<rrangle> $\rangle$ \<lceil> $\bigtriangledown$ \<rceil> $\bigtriangledown$ \<lfloor> $\bigtriangledown$ \<rfloor> $\bigtriangledown$ \<lparr> $\bigtriangledown$ \<rparr> $\bigtriangledown$ \<lbrakk> $\bigtriangledown$ \<rbrakk> $\bigtriangledown$ \<lbrace> $\bigtriangledown$ \<brace> $\bigtriangledown$ \<l blot> $\bigtriangledown$ \<r blot> $\bigtriangledown$ \<guillemotleft> $\ll$ \<guillemotright> $\gg$ \<bottom> $\bot$ \<top> $\top$ \<and> $\wedge$ \<And> $\wedge$ \<or> $\vee$ \<0r> $\vee$ \<forall> $\forall$ \<exists> $\exists$ \<not> $\neg$ \<nexists> $\#$ \<circle> $\bigcirc$ \<box> $\square$ \<diamond> $\diamond$ \<diamondop> $\diamond$ \<surd> $\sqrt{ }$ \<turnstile> $\vdash$ \<Turnstile> $\models$ \<turnstile> $\Vdash$ \<TTurnstile> \|= \<stileturn> $-$ \<le> $\leq$ \<ge> $\geq$ \</less> $\ll$ \<ggreater> $\gg$ \</lesssim> $\lesseqqgtr$ \<greatersim> $\gtrsim$ \</lessapprox> $\lesseqqgtr$ \<greaterapprox> $\gtrsim$ \</in> $\in$ \<notin> $\notin$ \</subset> $\sqsubset$ \<sup>: subset</sup> $\sqcap$ \</subseteq> $\sqsubseteq$ \<sup>:subseteq</sup> $\sqsupset$ \</sqsubsetset> $\sqcap$ \</sqsubsetseteq> $\sqcap$ \</inter> $\cap$ \</union> U  
\</squnion> U  
\</sqinter> 

\<setminus> \\\\propto\\\\uplus> \\\\sim\\\\doteq> \\\\simeq> \\\\approx\\\\cong\\\\equiv\\\\frown> \\\\Join> \\\\bowtie> \\\\prec\curlywedge\\\\preceq> \\\\succeq> \\\\parallel\\\\parallel\\\\interleace> \\\\bar{b}\bar{r}\bar{a}>\\\\pm\\\\times\\\\div\\\\cdot> \\\\star\\\\bullet\\\\ddagger\\\\hdd> \\\\unlhd> \\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft\\\\triangleleft $\S$ 

```txt
\<paragraph> ¶ \<exclamdown> i  
\<questiondown> i \<euro> €  
\<pounds> £ \<yen> ¥  
\<cent> € \<currency> α  
\<degree> ° \<hyphen> -  
\<amalg> II \<mho> U  
\<lozenge> ◇ \<wp> ψ  
\<wrong> ½ \<acute> '  
\<index> 1 \<dieresis> ''  
\<cedilla> , \<hungarumlaut> ''  
\<some> € \<bind> ≥  
\<then> ≥ \<Zcomp> °  
\<Zinj> → \<Zpinj> ++  
\<Zfinj> ++ \<Zsurj> →  
\<Zpsurj> → >> \<Zbjj> →  
\<Zpfun> → \<Zffun> +  
\<Zdres> < \<Zndres> ⇔  
\<Zrres> ▷ \<Znrres> ⋅  
\<Zspot> ● \<Zproject> ↑  
\<Zsemi> ° \<Ztypecolon> °  
\<Zhide> \\ \<Zcat> (√)  
\<Zinbag> E \<hole> □  
\<newline> ← \<comment> —  
\<proof> <proof> <open> <  
\<close> > \<checkmark> √  
\<crossmark> X 
```

# Bibliography



[1] P. Andrews. An Introduction to Mathematical Logic and Type Theory: to Truth through Proof. Computer Science and Applied Mathematics. Academic Press, 1986. 





[2] D. Aspinall. Proof General. http://proofgeneral.inf.ed.ac.uk/. 





[3] D. Aspinall. Proof General: A generic tool for proof development. In Tools and Algorithms for the Construction and Analysis of Systems (TACAS), volume 1785 of Lecture Notes in Computer Science, pages 38–42. Springer-Verlag, 2000. 





[4] C. Ballarin. Locales: A module system for mathematical theories. Journal of Automated Reasoning, 52(2):123–153, 2014. 





[5] G. Bauer and M. Wenzel. Calculational reasoning revisited — an Isabelle/Isar experience. In R. J. Boulton and P. B. Jackson, editors, Theorem Proving in Higher Order Logics: TPHOLs 2001, volume 2152 of Lecture Notes in Computer Science. Springer-Verlag, 2001. 





[6] S. Berghofer and T. Nipkow. Proof terms for simply typed higher order logic. In J. Harrison and M. Aagaard, editors, Theorem Proving in Higher Order Logics: TPHOLs 2000, volume 1869 of Lecture Notes in Computer Science, pages 38–52. Springer-Verlag, 2000. 





[7] M. Bezem and T. Coquand. Automating Coherent Logic. In G. Sutcliffe and A. Voronkov, editors, LPAR-12, volume 3835 of Lecture Notes in Computer Science. Springer-Verlag, 2005. 





[8] J. Biendarra, J. C. Blanchette, M. Desharnais, L. Panny, A. Popescu, and D. Traytel. Defining (Co)datatypes and Primitively (Co)recursive Functions in Isabelle/HOL. https://isabelle.in.tum.de/doc/datatypes.pdf. 





[9] J. C. Blanchette. Hammering Away: A User’s Guide to Sledgehammer for Isabelle/HOL. https://isabelle.in.tum.de/doc/sledgehammer.pdf. 





[10] J. C. Blanchette. Picking Nits: A User’s Guide to Nitpick for Isabelle/HOL. https://isabelle.in.tum.de/doc/nitpick.pdf. 





[11] R. S. Boyer and J. S. Moore. A Computational Logic Handbook. Academic Press, 1988. 





[12] A. Chaieb. Automated methods for formal proofs in simple arithmetics and algebra. PhD thesis, Technische Universität München, 2008. http://www4.in.tum.de/~chaieb/pubs/pdf/diss.pdf. 





[13] A. Chaieb and M. Wenzel. Context aware calculation and deduction — ring equalities via Gröbner Bases in Isabelle. In M. Kauers, M. Kerber, R. Miner, and W. Windsteiger, editors, Towards Mechanized Mathematical Assistants (CALCULEMUS 2007), volume 4573 of LNAI. Springer-Verlag, 2007. 





[14] A. Church. A formulation of the simple theory of types. Journal of Symbolic Logic, 5:56–68, 1940. 





[15] M. O. et al. An overview of the scala programming language. Technical Report IC/2004/64, EPFL Lausanne, Switzerland, 2004. 





[16] W. M. Farmer. The seven virtues of simple type theory. J. Applied Logic, 6(3):267–286, 2008. 





[17] K. Futatsugi, J. Goguen, J.-P. Jouannaud, and J. Meseguer. Principles of OBJ2. In Symposium on Principles of Programming Languages, pages 52–66, 1985. 





[18] G. Gentzen. Untersuchungen über das logische Schließen. Math. Zeitschrift, 1935. 





[19] M. J. C. Gordon. HOL: A machine oriented formulation of higher order logic. Technical Report 68, University of Cambridge Computer Laboratory, 1985. 





[20] M. J. C. Gordon and T. F. Melham, editors. Introduction to HOL: A Theorem Proving Environment for Higher Order Logic. Cambridge University Press, 1993. 





[21] F. Haftmann. Code generation from Isabelle theories. https://isabelle.in.tum.de/doc/codegen.pdf. 





[22] F. Haftmann. Haskell-style type classes with Isabelle/Isar. https://isabelle.in.tum.de/doc/classes.pdf. 





[23] F. Haftmann and M. Wenzel. Constructive type classes in Isabelle. In T. Altenkirch and C. McBride, editors, Types for Proofs and Programs, TYPES 2006, volume 4502 of LNCS. Springer, 2007. 





[24] B. Huffman and O. Kunčar. Lifting and Transfer: A Modular Design for Quotients in Isabelle/HOL. In Certified Programs and Proofs (CPP 2013), volume 8307 of Lecture Notes in Computer Science. Springer-Verlag, 2013. 





[25] A. Krauss. Defining Recursive Functions in Isabelle/HOL. https://isabelle.in.tum.de/doc/functions.pdf. 





[26] A. Krauss. Automating Recursive Definitions and Termination Proofs in Higher-Order Logic. PhD thesis, Institut für Informatik, Technische Universität München, Germany, 2009. 





[27] O. Kuncar. Correctness of Isabelle’s cyclicity checker: Implementability of overloading in proof assistants. In Proceedings of the 2015 Conference on Certified Programs and Proofs, CPP 2015, Mumbai, India, January 15-17, 2015, 2015. 





[28] O. Kuncar and A. Popescu. A consistent foundation for Isabelle/HOL. In C. Urban and X. Zhang, editors, Interactive Theorem Proving - 6th International Conference, ITP 2015, Nanjing, China, August 24-27, 2015, Proceedings, volume 9236 of Lecture Notes in Computer Science. Springer, 2015. 





[29] X. Leroy et al. The Objective Caml system – Documentation and user’s manual. http://caml.inria.fr/pub/docs/manual-ocaml/. 





[30] D. W. Loveland. Automated Theorem Proving: A Logical Basis. North-Holland Publishing Co., 1978. 





[31] U. Martin and T. Nipkow. Ordered rewriting and confluence. In M. E. Stickel, editor, 10th International Conference on Automated Deduction, LNAI 449, pages 366–380. Springer, 1990. 





[32] D. Matichuk, M. Wenzel, and T. C. Murray. An Isabelle proof method language. In G. Klein and R. Gamboa, editors, Interactive Theorem Proving - 5th International Conference, ITP 2014, Held as Part of the Vienna Summer of Logic, VSL 2014, Vienna, Austria, volume 8558 of LNCS. Springer, 2014. 





[33] D. Miller. A logic programming language with lambda-abstraction, function variables, and simple unification. Journal of Logic and Computation, 1(4), 1991. 





[34] R. Milner, M. Tofte, and R. Harper. The Definition of Standard ML. MIT Press, 1990. 





[35] W. Naraschewski and M. Wenzel. Object-oriented verification based on record subtyping in higher-order logic. In J. Grundy and M. Newey, editors, Theorem Proving in Higher Order Logics: TPHOLs ’98, volume 1479 of Lecture Notes in Computer Science. Springer-Verlag, 1998. 





[36] T. Nipkow. Functional unification of higher-order patterns. In M. Vardi, editor, Eighth Annual Symposium on Logic in Computer Science, pages 64–74. IEEE Computer Society Press, 1993. 





[37] T. Nipkow. Structured Proofs in Isar/HOL. In H. Geuvers and F. Wiedijk, editors, Types for Proofs and Programs (TYPES 2002), volume 2646 of Lecture Notes in Computer Science, pages 259–278. Springer-Verlag, 2003. 





[38] T. Nipkow, L. C. Paulson, and M. Wenzel. Isabelle/HOL — A Proof Assistant for Higher-Order Logic. Springer, 2002. LNCS 2283. 





[39] T. Nipkow, L. C. Paulson, and M. Wenzel. Isabelle/HOL: A Proof Assistant for Higher-Order Logic, volume 2283 of Lecture Notes in Computer Science. Springer-Verlag, 2002. 





[40] T. Nipkow and C. Prehofer. Type reconstruction for type classes. Journal of Functional Programming, 5(2):201–224, 1995. 





[41] D. C. Oppen. Pretty printing. ACM Transactions on Programming Languages and Systems, 2(4), 1980. 





[42] L. C. Paulson. Isabelle’s Logics. https://isabelle.in.tum.de/doc/logics.pdf. 





[43] L. C. Paulson. Isabelle’s Logics: FOL and ZF. https://isabelle.in.tum.de/doc/logics-ZF.pdf. 





[44] L. C. Paulson. Natural deduction as higher-order resolution. Journal of Logic Programming, 3:237–258, 1986. 





[45] L. C. Paulson. The foundation of a generic theorem prover. Journal of Automated Reasoning, 5(3):363–397, 1989. 





[46] L. C. Paulson. Isabelle: The next 700 theorem provers. In P. Odifreddi, editor, Logic and Computer Science, pages 361–386. Academic Press, 1990. 





[47] L. C. Paulson. ML for the Working Programmer. Cambridge University Press, 2nd edition, 1996. https://www.cl.cam.ac.uk/~lp15/MLbook. 





[48] F. J. Pelletier. Seventy-five problems for testing automatic theorem provers. Journal of Automated Reasoning, 2:191–216, 1986. Errata, JAR 4 (1988), 235–236 and JAR 18 (1997), 135. 





[49] S. Peyton Jones et al. The Haskell 98 language and libraries: The revised report. Journal of Functional Programming, 13(1):0–255, Jan 2003. http://www.haskell.org/definition/. 





[50] A. Pitts. The HOL logic. In M. J. C. Gordon and T. F. Melham, editors, Introduction to HOL: A Theorem Proving Environment for Higher Order Logic, pages 191–232. Cambridge University Press, 1993. 





[51] C. Runciman, M. Naylor, and F. Lindblad. Smallcheck and Lazy Smallcheck: Automatic exhaustive testing for small values. In Proceedings of the First ACM SIGPLAN Symposium on Haskell (Haskell 2008), pages 37–48. ACM, 2008. 





[52] P. Schroeder-Heister. A natural extension of natural deduction. Journal of Symbolic Logic, 49(4), 1984. 





[53] D. Traytel, S. Berghofer, and T. Nipkow. Extending Hindley-Milner Type Inference with Coercive Structural Subtyping. In H. Yang, editor, APLAS 2011, volume 7078 of Lecture Notes in Computer Science, pages 89–104, 2011. 





[54] M. Wenzel. The Isabelle System Manual. https://isabelle.in.tum.de/doc/system.pdf. 





[55] M. Wenzel. The Isabelle/Isar Implementation. https://isabelle.in.tum.de/doc/implementation.pdf. 





[56] M. Wenzel. Isabelle/jEdit. https://isabelle.in.tum.de/doc/jedit.pdf. 





[57] M. Wenzel. Type classes and overloading in higher-order logic. In E. L. Gunter and A. Felty, editors, Theorem Proving in Higher Order Logics: TPHOLs ’97, volume 1275 of Lecture Notes in Computer Science. Springer-Verlag, 1997. 





[58] M. Wenzel. Isar — a generic interpretative approach to readable formal proof documents. In Y. Bertot, G. Dowek, A. Hirschowitz, C. Paulin, and L. Thery, editors, Theorem Proving in Higher Order Logics: TPHOLs ’99, volume 1690 of Lecture Notes in Computer Science. Springer-Verlag, 1999. 





[59] M. Wenzel. Isabelle/Isar — a versatile environment for human-readable formal proof documents. PhD thesis, Institut für Informatik, Technische Universität München, 2002. https://mediatum.ub.tum.de/doc/601724/601724.pdf. 





[60] M. Wenzel. Isabelle/Isar — a generic framework for human-readable proof documents. In R. Matuszewski and A. Zalewska, editors, From Insight to Proof — Festschrift in Honour of Andrzej Trybulec, volume 10(23) of Studies in Logic, Grammar, and Rhetoric. University of Białystok, 2007. http://www.in.tum.de/~wenzelm/papers/isar-framework.pdf. 





[61] M. Wenzel. Isabelle/jEdit — a Prover IDE within the PIDE framework. In J. Jeuring et al., editors, Conference on Intelligent Computer Mathematics (CICM 2012), volume 7362 of LNAI. Springer, 2012. 





[62] M. Wenzel and L. C. Paulson. Isabelle/Isar. In F. Wiedijk, editor, The Seventeen Provers of the World, LNAI 3600. Springer-Verlag, 2006. 





[63] F. Wiedijk. Mizar: An impression. Unpublished paper, 1999. http://www.cs.kun.nl/~freek/mizar/mizarintro.ps.gz. 



# Index

- (method), 149 

. (command), 146 

.. (command), 146 

?case (variable), 151 

?thesis (variable), 142 

_ (fact), 138 

{ (command), 132 

} (command), 132 

abbrev (antiquotation), 72 

abbreviation (command), 98, 254 

abbrevs (keyword), 93 

abs_def (attribute), 209, 210 

addafter (ML infix), 245 

addbefore (ML infix), 245 

addloop (ML infix), 230 

addSafter (ML infix), 245 

addSbefore (ML infix), 245 

addSolver (ML infix), 229 

addss (ML), 245 

addSSolver (ML infix), 229 

addSss (ML), 245 

addSWrapper (ML infix), 245 

addWrapper (ML infix), 245 

adhoc_overloading (command), 266 

algebra (HOL attribute), 301 

algebra (HOL method), 301 

alias (command), 130 

also (command), 142 

altstring (syntax), 53, 53, 63 

and (keyword), 62, 134 

antiquotation (syntax), 74 

antiquotation_body (syntax), 75 

any (inner syntax), 188, 190 

apply (command), 137, 138, 166 

apply_end (command), 166 

aprop (inner syntax), 189, 190 

args (syntax), 63 

arith (HOL attribute), 299 

arith (HOL method), 299 

arity (syntax), 58 

assms (fact), 139 

assume (command), 133 

assumes (element), 104 

assumption (inference), 32 

assumption (method), 149 

atom (syntax), 62 

atomize (attribute), 246 

atomize (method), 246 

attribute_setup (command), 119 

attributes (syntax), 63 

auto (method), 239 

axiomatization (command), 100, 128 

axmdecl (syntax), 64 

back (command), 166 

bash_function (antiquotation), 73 

best (method), 239 

bestsimp (method), 239 

binder (keyword), 184 

blast (method), 239 

bold (antiquotation), 73 

break (antiquotation option), 81 

build (tool), 70 

bundle (antiquotation), 72 

bundle (command), 96 

by (command), 146 

calculation (fact), 142 

cartouche (antiquotation option), 81 

cartouche (antiquotation), 73 

cartouche (inner syntax), 187 

cartouche (syntax), 53, 54, 63, 74 

case (command), 151, 153 

case_conclusion (attribute), 153 

case_names (attribute), 153, 164 

case_tac (HOL method), 303 

cases (attribute), 161 

cases (method), 155, 156 

chapter (command), 70 

cite (antiquotation), 73 

citep (antiquotation), 73 

citet (antiquotation), 73 

clamod (syntax), 240 

clarify (method), 243 

clarify_step (method), 244 

clarsimp (method), 243 

clasimpmod (syntax), 241 

class (antiquotation), 72 

class (command), 113 

class_deps (command), 113 

class_name (inner syntax), 190 

class_syntax (ML antiquotation), 202 

classdecl (syntax), 57 

cleaning (HOL method), 288 

code (HOL attribute), 307 

code_abbrev (HOL attribute), 307 

code_datatype (HOL command), 307 

code_deps (HOL command), 307 

code_identifier (HOL command), 307 

code_monad (HOL command), 307 

code_post (HOL attribute), 307 

code_pred (HOL command), 307 

code_printing (HOL command), 307 

code_reflect (HOL command), 307 

code_reserved (HOL command), 307 

code_runtime_trace (HOL attribute), 307 

code_simp_trace (HOL attribute), 307 

code_thms (HOL command), 307 

code_timing (HOL attribute), 307 

code_unfold (HOL attribute), 307 

coercion (HOL attribute), 298 

coercion_args (HOL attribute), 298 

coercion_delete (HOL attribute), 298 

coercion_enabled (HOL attribute), 298 

coercion_map (HOL attribute), 298 

coherent (HOL method), 302 

coinduct (attribute), 161 

coinduct (method), 156 

coinductive (HOL command), 253 

coinductive_set (HOL command), 253 

compile_generated_files (command), 123 

cong (attribute), 218 

consider (command), 162 

const (antiquotation), 72 

const_syntax (ML antiquotation), 202 

constrains (element), 104 

consts (command), 117 

consumes (attribute), 153 

context (command), 94, 156 

context_elem (syntax), 106 

contradiction (method), 239 

contributor (document marker), 84 

corollary (command), 138 

creator (document marker), 84 

cut_tac (method), 171 

datatype (HOL command), 258 

date (document marker), 84 

declaration (command), 101 

declare (command), 101 

deepen (method), 239 

default_sort (command), 127 

defer (command), 166 

define (command), 133 

defines (element), 104 

definition (command), 98 

defn (attribute), 98 

delloop (ML infix), 230 

delSWrapper (ML infix), 245 

delWrapper (ML infix), 245 

descending (HOL method), 288 

descending_setup (HOL method), 288 

description (document marker), 84 

dest (attribute), 237 

dest (Pure attribute), 149 

display (antiquotation option), 81 

document_tags (system option), 85 

done (command), 166 

drule (method), 208 

drule_tac (method), 171 

elim (attribute), 237 

elim (method), 208 

elim (Pure attribute), 149 

elim_format (Pure attribute), 210 

elim_resolution (inference), 32 

embedded (syntax), 56 

emph (antiquotation), 73 

end (global command), 91 

end (local command), 94, 115 

erule (method), 208 

erule_tac (method), 171 

eta_contract (antiquotation option), 81 

eta_contract (attribute), 177, 201 

expand (inference), 34 

experiment (command), 104 

export (inference), 34 

export (tool), 316 

export_code (command), 123 

export_code (HOL command), 307 

export_generated_files (command), 123 

external_file (command), 123 

fact (method), 63, 149 

fail (method), 208 

fast (method), 239 

fastforce (method), 239 

file (antiquotation), 73 

finally (command), 142 

find_consts (command), 66 

find_theorems (command), 66 

find_unused_assms (HOL command), 293 

finish (inference), 31 

fix (command), 133 

fixes (element), 104 

float (syntax), 53 

float_const (inner syntax), 187 

float_token (inner syntax), 186 

fold (method), 208 

folded (attribute), 210 

for (keyword), 128 

for_fixes (syntax), 65 

force (method), 239 

from (command), 136 

frule (method), 208 

frule_tac (method), 171 

full_prf (antiquotation), 72 

full_prf (command), 174 

fun (HOL command), 257 

fun_cases (HOL command), 257 

function (HOL command), 257 

functor (HOL command), 2 

generate_file (command), 123 

global_interpretation (command), 108 

goal_cases (method), 149 

goal_spec (syntax), 146 

goals (antiquotation), 72 

goals_limit (antiquotation option), 82 

goals_limit (attribute), 177 

have (command), 138 

help (command), 51 

hence (command), 138 

hide_class (command), 130 

hide_const (command), 130 

hide_fact (command), 130 

hide_type (command), 130 

hypsubst (method), 211 

id (inner syntax), 186 

idt (inner syntax), 189, 190, 191 

idts (inner syntax), 189, 191 

if (keyword), 142, 165 

iff (attribute), 237 

in (keyword), 95 

include (command), 96 

includes (keyword), 96 

includes (syntax), 94, 97, 140 

including (command), 96 

ind_cases (HOL method), 303 

indent (antiquotation option), 82 

index (inner syntax), 189, 190 

induct (attribute), 161 

induct (method), 138, 155, 156 

induct_simp (attribute), 160 

induct_tac (HOL method), 303 

induction (method), 156 

induction_schema (HOL method), 262 

inductive (HOL command), 253 

inductive_cases (HOL command), 303 

inductive_set (HOL command), 253 

infix (keyword), 184 

infixl (keyword), 184 

infixr (keyword), 184 

init (inference), 31 

injection (HOL method), 288 

insert (method), 208 

inst (syntax), 58 

inst_step (method), 244 

instance (command), 113, 129 

instantiation (command), 113, 129 

insts (syntax), 59 

int (syntax), 55 

interpret (command), 108 

intro (attribute), 237 

intro (method), 208 

intro (Pure attribute), 149 

intro_classes (method), 113, 148 

intro_locales (method), 108, 148 

iprover (HOL method), 300 

is (keyword), 135 

judgment (command), 246 

keywords (keyword), 93 

lemma (antiquotation), 72 

lemma (command), 138 

lemmas (command), 128 

let (command), 135 

lexicographic_order (HOL method), 262 

license (document marker), 84 

lift_definition (HOL command), 280, 281, 283, 284 

lifting (HOL method), 288 

lifting_forget (HOL command), 280 

lifting_restore (HOL attribute), 280 

lifting_setup (HOL method), 288 

lifting_update (HOL command), 280 

linarith_split (HOL attribute), 299 

local_setup (command), 119 

locale (antiquotation), 72 

locale (command), 104 

locale (syntax), 105 

locale_deps (command), 104 

locale_expr (syntax), 102 

logic (inner syntax), 189, 190 

long_ident (syntax), 53, 186 

longid (inner syntax), 186 

margin (antiquotation option), 82 

marker (syntax), 83 

marker_body (syntax), 84 

meson (HOL method), 300 

method (syntax), 145 

method_facts (fact), 136 

method_setup (command), 152 

metis (HOL method), 300 

mixfix (syntax), 180 

mixfix_properties (syntax), 182, 183 

mkroot (tool), 70 

ML (antiquotation), 72 

ML (command), 119 

ML_command (command), 119 

ML_debugger (attribute), 119 

ML_debugger (system option), 122 

ML_def (antiquotation), 72 

ML_environment (attribute), 119 

ML_exception_debugger (attribute), 119 

ML_exception_trace (attribute), 119 

ML_export (command), 119 

ML_file (command), 119 

ML_file_debug (command), 119 

ML_file_no_debug (command), 119 

ML_functor (antiquotation), 72 

ML_functor_def (antiquotation), 72 

ML_functor_ref (antiquotation), 72 

ML_infix (antiquotation), 72 

ML_infix_def (antiquotation), 72 

ML_infix_ref (antiquotation), 72 

ML_prf (command), 119 

ML_print_depth (attribute), 119 

ML_ref (antiquotation), 72 

ML_source_trace (attribute), 119 

ML_structure (antiquotation), 72 

ML_structure_def (antiquotation), 72 

ML_structure_ref (antiquotation), 72 

ML_text (antiquotation), 72 

ML_type (antiquotation), 72 

ML_type_def (antiquotation), 72 

ML_type_ref (antiquotation), 72 

ML_val (command), 119 

mode (antiquotation option), 81 

modes (syntax), 175 

mono (HOL attribute), 253 

moreover (command), 142 

multi_specs (syntax), 65 

name (syntax), 54, 74 

named_inst (syntax), 59 

named_insts (syntax), 59 

named_theorems (command), 128 

names_long (antiquotation option), 81 

names_long (attribute), 177 

names_short (antiquotation option), 81 

names_short (attribute), 177 

names_unique (antiquotation option), 81 

names_unique (attribute), 177 

nat (syntax), 53, 53, 186 

next (command), 132 

nitpick (HOL command), 293 

nitpick_params (HOL command), 293 

no_adhoc_overloading (command), 266 

no_notation (command), 185 

no_syntax (command), 197 

no_translations (command), 197 

no_type_notation (command), 185 

no_vars (attribute), 210 

nocite (antiquotation), 73 

nonterminal (command), 197 

notation (command), 185 

note (command), 136 

notepad (command), 131 

notes (element), 104 

nothing (fact), 138 

num_const (inner syntax), 187 

num_token (inner syntax), 186 

obtain (command), 162 

obtain_case (syntax), 141 

obtain_clauses (syntax), 140 

obtains (element), 139 

OF (attribute), 149 

of (attribute), 149 

old_rep_datatype (HOL command), 267 

oops (command), 133 

opening (syntax), 94, 97, 105, 113 

oracle (command), 129 

output (keyword), 198 

overloaded (syntax), 274 

overloading (command), 117 

par_name (syntax), 55 

paragraph (command), 70 

params (attribute), 153 

parse_ast_translation (command), 202 

parse_translation (command), 202 

partial_function (HOL command), 263 

partial_function_mono (HOL attribute), 263 

partiality_descending (HOL method), 288 

partiality_descending_setup (HOL method), 288 

pat_completeness (HOL method), 262 

prefer (command), 166 

presume (command), 133 

prf (antiquotation), 72 

prf (command), 174 

primrec (HOL command), 257 

print_abbrevs (command), 98 

print_antiquotations (command), 73 

print_ast_translation (command), 202 

print_attributes (command), 66 

print_bundles (command), 96 

print_cases (command), 153 

print_claset (command), 237 

print_classes (command), 113 

print_codeproc (HOL command), 307 

print_codesetup (HOL command), 307 

print_commands (command), 51 

print_definitions (command), 66 

print_defn_rules (command), 98 

print_facts (command), 66 

print_induct_rules (command), 161 

print_inductives (command), 253 

print_interps (command), 108 

print_locale (command), 104 

print_locales (command), 104 

print_methods (command), 66 

print_options (command), 207 

print_quot_maps (HOL command), 280 

print_quotconsts (HOL command), 288 

print_quotients (HOL command), 280 

print_quotientsQ3 (HOL command), 288 

print_quotmapsQ3 (HOL command), 288 

print_record (HOL command), 270 

print_rules (command), 149 

print_simpset (command), 218 

print_state (command), 174 

print_statement (command), 138 

print_syntax (command), 192, 201, 203 

print_term_bindings (command), 66 

print_theorems (command), 66 

print_theory (command), 66 

print_trans_rules (command), 142 

print_translation (command), 202 

Print_Mode.with_modes (ML), 179 

print_mode_value (ML), 179 

private (keyword), 94 

proof 

fake, 148 

standard, 148 

terminal, 148 

trivial, 148 

proof (command), 137, 138, 146, 146, 150 

prop (antiquotation), 72 

prop (command), 174 

prop (inner syntax), 188, 190 

prop (syntax), 58 

prop_pat (syntax), 61 

proposition (command), 138 

props (syntax), 61 

props’ (syntax), 62 

pttrn (inner syntax), 189, 191 

pttrns (inner syntax), 189, 191 

qed (command), 146, 146 

qualified (keyword), 94 

quickcheck (HOL command), 293 

quickcheck_generator (HOL command), 293 

quickcheck_params (HOL command), 293 

quot_del (HOL attribute), 280 

quot_lifted (HOL attribute), 288 

quot_map (HOL attribute), 280 

quot_preserve (HOL attribute), 288 

quot_respect (HOL attribute), 288 

quot_thm (HOL attribute), 288 

quotes (antiquotation option), 81 

quotient_definition (HOL command), 288 

quotient_type (HOL command), 278 

rail (antiquotation), 86 

raw_tactic (method), 171 

real (syntax), 55 

recdef (HOL command), 264 

recdef_cong (HOL attribute), 266 

recdef_simp (HOL attribute), 266 

recdef_wf (HOL attribute), 266 

record (HOL command), 270 

regularize (HOL method), 288 

relation (HOL method), 262 

relator_distr (HOL attribute), 280 

relator_domain (HOL attribute), 285, 287 

relator_eq (HOL attribute), 285 

relator_eq_onp (HOL attribute), 280 

relator_mono (HOL attribute), 280 

rename_tac (method), 171 

resolution (inference), 31 

rotate_tac (method), 171 

rotated (attribute), 210 

rule (attribute), 237 

rule (HOL method), 147 

rule (method), 239 

rule (Pure attribute), 149 

rule (Pure method), 138, 147, 148, 149, 150 

rule_format (attribute), 246 

rule_tac (method), 171 

rulify (attribute), 246 

safe (method), 243 

safe_step (method), 244 

schematic_goal (command), 138 

section (command), 70 

session (antiquotation), 73 

setloop (ML infix), 230 

setSolver (ML infix), 229 

setSSolver (ML infix), 229 

setup (command), 119 

setup_lifting (HOL command), 280 

short_ident (syntax), 53, 186 

show (command), 134, 138, 146 

show_abbrevs (antiquotation option), 81 

show_abbrevs (attribute), 177 

show_brackets (attribute), 177 

show_consts (attribute), 177 

show_hyps (attribute), 177 

show_main_goal (attribute), 177 

show_markup (attribute), 177 

show_question_marks (attribute), 177 

show_sorts (antiquotation option), 81 

show_sorts (attribute), 177 

show_structs (antiquotation option), 81 

show_tags (attribute), 177 

show_types (antiquotation option), 81 

show_types (attribute), 177 

show_variants (attribute), 266 

shows (element), 139 

simp (attribute), 218 

simp (method), 213 

simp (Pure method), 213 

simp_all (method), 213 

simp_all (Pure method), 213 

simp_break (attribute), 223 

simp_debug (attribute), 223 

simp_depth_limit (attribute), 213 

simp_trace (attribute), 223 

simp_trace_depth_limit (attribute), 223 

simp_trace_new (attribute), 223 

simplified (attribute), 232 

Simplifier.mk_solver (ML), 229 

Simplifier.prems_of (ML), 228 

Simplifier.set_subgoaler (ML), 228 

Simplifier.set_term_ord (ML), 222 

simpmod (syntax), 214 

simproc_setup (command), 225 

simproc_setup (ML antiquotation), 225, 226 

simproc_setup (syntax), 225 

simproc_setup_id (syntax), 226 

size_change (HOL method), 262 

sledgehammer (HOL command), 291 

sledgehammer_params (HOL command), 291 

sleep (method), 208 

slow (method), 239 

slow_step (method), 244 

slowsimp (method), 239 

SML_file (command), 119 

SML_file_debug (command), 119 

SML_file_no_debug (command), 119 

solve_direct (HOL command), 291 

solver (ML type), 229 

sorry (command), 133, 146 

sort (inner syntax), 190, 191 

sort (syntax), 57 

source (antiquotation option), 82 

source_cartouche (antiquotation option), 82 

spec_prems (syntax), 66 

specification (HOL command), 267 

specification (syntax), 66 

split (attribute), 218 

split (method), 211, 215 

split_format (HOL attribute), 304 

Splitter.add_split (ML), 230 

Splitter.add_split_bang (ML), 230 

Splitter.del_split (ML), 230 

standard (method), 146 

step (method), 244 

str_token (inner syntax), 186 

string (syntax), 53, 53 

string_token (inner syntax), 186 

structure (keyword), 107, 190 

structured_spec (syntax), 65 

subclass (command), 113 

subgoal (command), 168 

subgoal_tac (method), 171 

subgoals (antiquotation), 72 

sublocale (command), 108 

subparagraph (command), 70 

subproofs (method), 149 

subsection (command), 70 

subst (method), 211 

subsubsection (command), 70 

succeed (method), 208 

supply (command), 166 

swapped (attribute), 237 

sym_ident (syntax), 53 

syntax (command), 197 

syntax_ambiguity_limit (attribute), 193 

syntax_ambiguity_warning (attribute), 193 

syntax_ast_stats (attribute), 197 

syntax_ast_trace (attribute), 197 

syntax_const (ML antiquotation), 202 

syntax_declaration (command), 101 

system_name (syntax), 55 

system_option (antiquotation), 73 

tactic (method), 171 

tag (document marker), 85 

tagged (attribute), 210 

tags (syntax), 84 

target (syntax), 94 

term (antiquotation), 72 

term (command), 174 

term (syntax), 58 

term abbreviations, 136 

term_pat (syntax), 61 

term_type (antiquotation), 72 

term_var (syntax), 53, 53 

termination (HOL command), 257 

termination_simp (HOL attribute), 262 

text (antiquotation), 72, 73 

text (command), 70, 82 

text (syntax), 56 

text_raw (command), 70, 82 

that (fact), 142, 165 

THEN (attribute), 210 

then (command), 136 

theorem (command), 138 

theory (antiquotation), 72 

theory (command), 91 

thesis (variable), 136 

thin_tac (method), 171 

this (fact), 131, 136 

this (method), 149 

this (variable), 136 

thm (antiquotation), 72 

thm (command), 174 

thm (syntax), 64 

thm_deps (command), 66 

thm_oracles (command), 129 

thmbind (syntax), 64 

thmdecl (syntax), 64 

thmdef (syntax), 64 

thms (syntax), 64 

thus (command), 138 

thy_deps (command), 91 

tid (inner syntax), 186 

title (document marker), 84 

trace_locales (attribute), 108 

transfer (HOL method), 285 

transfer’ (HOL method), 285 

Transfer.transferred (HOL attribute), 285 

transfer_domain_rule (HOL attribute), 285 

transfer_end (HOL method), 285 

transfer_prover (HOL method), 285 

transfer_prover_end (HOL method), 285 

transfer_prover_start (HOL method), 285 

transfer_rule (HOL attribute), 285 

transfer_start (HOL method), 285 

transfer_step (HOL method), 285 

translations (command), 197 

try (HOL command), 291 

try0 (HOL command), 291 

tvar (inner syntax), 186 

txt (command), 70, 82 

typ (antiquotation), 72 

typ (command), 174 

type (antiquotation), 72 

type (inner syntax), 189, 191 

type (syntax), 58 

type_alias (command), 130 

type_ident (syntax), 53, 186 

type_name (inner syntax), 190 

type_notation (command), 185 

type_synonym (command), 127 

type_syntax (ML antiquotation), 202 

type_var (syntax), 53, 53, 186 

typeargs (syntax), 60 

typeargs_sorts (syntax), 60 

typed_print_translation (command), 202 

typedecl (command), 127, 128 

typedef (command), 128 

typedef (HOL command), 274 

typeof (antiquotation), 72 

typespec (syntax), 60 

typespec_sorts (syntax), 60 

ultimately (command), 142 

unfold (method), 137, 208 

unfold_locales (method), 108 

unfolded (attribute), 210 

unfolding (command), 136 

unify_search_bound (attribute), 248 

unify_trace (attribute), 248 

unify_trace_bound (attribute), 248 

unify_trace_simp (attribute), 248 

unify_trace_types (attribute), 248 

untagged (attribute), 210 

untransferred (HOL attribute), 285 

unused_thms (command), 66 

url (antiquotation), 73 

use (method), 136 

using (command), 136 

value (HOL command), 77, 293 

values (HOL command), 293 

var (inner syntax), 186 

var (syntax), 186 

vars (syntax), 61 

verbatim (antiquotation), 73 

verbatim (syntax), 53, 53 

when (keyword), 142 

where (attribute), 149 

with (command), 136 

wrapper (ML type), 245 

write (command), 185 
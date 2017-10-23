In algebra, a cyclic group or monogenous group is a group that is generated by a single element.[1] That is, it consists of a set of elements with a single invertible associative operation, and it contains an element g such that every other element of the group may be obtained by repeatedly applying the group operation or its inverse to g. Each element can be written as a power of g in multiplicative notation, or as a multiple of g in additive notation. This element g is called a generator of the group.[1]


Every infinite cyclic group is isomorphic to the additive group of Z, the integers. Every finite cyclic group of order n is isomorphic to the additive group of Z/nZ, the integers modulo n. Every cyclic group is an abelian group (meaning that its group operation is commutative), and every finitely generated abelian group is a direct product of cyclic groups.


In mathematics, a discrete subgroup of a topological group G is a subgroup H such that there is an open cover of H in which every open subset contains exactly one element of H; in other words, the subspace topology of H in G is the discrete topology. For example, the integers, Z, form a discrete subgroup of the reals, R (with the standard metric topology), but the rational numbers, Q, do not. A discrete group is a topological group G equipped with the discrete topology.

Any group can be given the discrete topology. Since every map from a discrete space is continuous, the topological homomorphisms between discrete groups are exactly the group homomorphisms between the underlying groups. Hence, there is an isomorphism between the category of groups and the category of discrete groups. 
In commutative algebra and field theory, the Frobenius endomorphism (after Ferdinand Georg Frobenius) is a special endomorphism of commutative rings with prime characteristic p, an important class which includes finite fields. The endomorphism maps every element to its p-th power. In certain contexts it is an automorphism, but this is not true in general.

The Galois group of an extension of finite fields is generated by an iterate of the Frobenius automorphism. First, consider the case where the ground field is the prime field. Let Fq be the finite field of q elements, where q = pe. The Frobenius automorphism F of Fq fixes the prime field Fp, so it is an element of the Galois group Gal(Fq/Fp). In fact, since Fq× is cyclic with q-1 elements, we know that the Galois group is cyclic and F is a generator. The order of F is e because F e acts on an element x by sending it to xq, and this is the identity on elements of Fq. Every automorphism of Fq is a power of F, and the generators are the powers F i with i coprime to e.

Now consider the finite field Fq f as an extension of Fq. The Frobenius automorphism F of Fq f does not fix the ground field Fq, but its e-th iterate F e does. The Galois group Gal(Fq f /Fq) is cyclic of order f and is generated by F e. It is the subgroup of Gal(Fq f /Fp) generated by F e. The generators of Gal(Fq f /Fq) are the powers F ei where i is coprime to f.

The Frobenius automorphism is not a generator of the absolute Galois group

    Gal ⁡ ( F q ¯ / F q ) , {\displaystyle \operatorname {Gal} \left({\overline {\mathbf {F} _{q}}}/\mathbf {F} _{q}\right),} \operatorname {Gal}\left(\overline {{\mathbf {F}}_{q}}/{\mathbf {F}}_{q}\right),

because this Galois group is

    Z ^ = lim ← n ⁡ Z / n Z , {\displaystyle {\widehat {\mathbf {Z} }}=\textstyle \varprojlim _{n}\mathbf {Z} /n\mathbf {Z} ,} \widehat {{\mathbf {Z}}}=\textstyle \varprojlim _{n}{\mathbf {Z}}/n{\mathbf {Z}},

which is not cyclic. However, because the Frobenius automorphism is a generator of the Galois group of every finite extension of Fq, it is a generator of every finite quotient of the absolute Galois group. Consequently, it is a topological generator in the usual Krull topology on the absolute Galois group.
Galois theory

An nth root of unity may be thought of as a complex number whose nth power is 1. 
That is, it is a root of the polynomial xn − 1. 

The nth roots of unity form a cyclic group of order n under multiplication. 
For example: 
the polynomial 
		0 = z3 − 1 
factors as 
		(z − s0)(z − s1)(z − s2)
where	
		s = e2πi/3
		
the set		
		{s0, s1, s2} 
forms a cyclic group under multiplication. 

The Galois group of the field extension of the rational numbers, generated by the nth roots of unity, forms a different group. 

It is isomorphic to the multiplicative group modulo n, which has order φ(n) and is cyclic for some but not all n.

A field extension is called a cyclic extension if:
	- its Galois group is a cyclic group. 

The Galois group of every finite extension 
of a finite field 
is finite and cyclic, 
with an iterate of the Frobenius endomorphism as its generator

Conversely, given a finite field F and a finite cyclic group G, there is a finite field extension of F whose Galois group is G.
In mathematics, a cover of a set X {\displaystyle X} X is a collection of sets whose union contains X {\displaystyle X} X as a subset. Formally, if

    C = { U α : α ∈ A } {\displaystyle C=\lbrace U_{\alpha }:\alpha \in A\rbrace } C=\lbrace U_{\alpha }:\alpha \in A\rbrace 

is an indexed family of sets U α {\displaystyle U_{\alpha }} U_{\alpha }, then C {\displaystyle C} C is a cover of X {\displaystyle X} X if

    X ⊆ ⋃ α ∈ A U α . {\displaystyle X\subseteq \bigcup _{\alpha \in A}U_{\alpha }.} X \subseteq \bigcup_{\alpha \in A}U_{\alpha}. 
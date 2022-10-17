# Simulation extractability of zkSNARKs

## Motivation
### Relevance of simulation extractability.
Most zkSNARKs are shown only to satisfy a standard knowledge soundness property.
Intuitively, this guarantees that a prover that creates a valid proof
in isolation knows a valid witness. However, deployments of zkSNARKs in
real-world applications, unless they are carefully designed to have
application-specific malleability protection, (Ben-Sasson et al. 2014),
require a stronger property -- simulation-extractability (SE) -- that
corresponds much more closely to existential unforgeability of signatures.

This correspondence is made precise by SoK, which uses an NP-language instance
as the public verification key. Instead of signing with the secret key, SoK
signing requires knowledge of the NP-witness. Intuitively, an SoK is thus a
proof of knowledge (PoK) of a witness that is tied to a message. In fact, many
signatures schemes, e.g., Schnorr, can be read as SoK for a specific hard
relation, e.g., DL (Dodis et al. 2010). To model strong existential unforgeability
of SoK signatures, even when given an oracle for obtaining signatures on
different instances, an attacker must not be able to produce new signatures.
Chase and Lysyanskaya (2006) model this via the notion of simulation
extractability which guarantees extraction of a witness even in the presence of
simulated signatures.

In practice, an adversary against a zkSNARK system also has access to proofs
computed by honest parties that should be modeled as simulated proofs. The
definition of knowledge soundness (KS) ignores the ability of an adversary to
see other valid proofs that may occur in real-world applications. For instance,
in applications of zkSNARKs in privacy-preserving blockchains, proofs are
posted on-chain for all blockchain participants to see. We thus argue that SE
is a much more suitable notion for robust protocol design. We also claim that
SE has primarily an intellectual cost, as it is harder to prove SE than
KS---another analogy here is IND-CCA vs IND-CPA security for encryption.
However, we will show that the proof systems we consider are SE out-of-the-box.

### SE zkSNARKs 

Recently, Ganesh et al. (SCN 2022) shown that Plonk, Marlin, Sonic are
simulation-extractable out-of-the-box. Namely, no transformation, that would
inevitably worse the zkSNARK's performance, is needed. More generally, the
authors prove that any zkSNARK that is 
- rewinding-based knowledge sound
- has unique response property, and
- trapdoor less zero knowledge
is simulation extractable. 


## Required properties
### unique-response property
After $k$ rounds the prover sends messages that are determined by the previously sent 
### trapdoor-less zero knowledge
### forking soundness 

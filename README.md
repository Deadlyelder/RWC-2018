# RWC-2018
Collection of notes that were jotted down at the [Real World Crypto (RWC)](https://rwc.iacr.org/index.html) 2018, Zurich

## Day 1

The first session was about `Key Management` which started with a talk by Shay Gueron (Amazon) about the cryptography that empowers the AWS cloud.
NIST has provided recommendation for the AES GCM mode that says the total number of instantiations of the AE with a
single key must not exceed 2^32. The problem is that Amazon uses the AES-256-GCM with random nonces for its AWS key
management service which makes it infeasible to have the desired level of security across its wide user base (More info about the problem:
        AES-GCM Forbidden attack [1]). The solution as developed and built by Amazon is to derive a new key for each encryption by applying a `kdf` function to the master key and the nonce. This solution improves the security bounds by a large degree by allowing users on the scale of 2^40 to securely encrypt 2^50 messages *each*. The full paper about the solution is available online [2].

The next talk within the session was about Google's internal KMS system by Anand Kanagala (Google). The presentation
itself was a form of storyboard that described the (in)famous Gmail outage [3] that happened due to one small bug. The lesson
learnt from this is that a small bug can make a dramatic impact on billions of accounts around the globe. The talk
continued with the precautions that were taken which required changing the whole KWS system of Google; not fully related
to cryptography to be honest... The talk also introduced a new crypto library called CrunchyCrypt [4], that is built with key-versioning which is the solution that allows horizontal scaling for stateless servers. *Fun fact: Google has other crypto libraries like Keyczar [5] and Tink [6], which as some participants pointed out, makes it confusing which one to recommend.*

That ended the `Key Management` session and now was the turn for the exciting session of `Cryptocurrencies`.

The very first talk was given by Andrew Poelstra (Blockstream) about the new-crypto currency that was proposed by
(yet-another) anonymous person on Tor in the form of a text file, the Mimblewimble [7]. It was truly fascinating especially
since it actually works (no kidding). Andrew explained in very great details the fundamental working on this new crypto
currency that is in the competition. Furthermore, as with every anonymous founder of cryptocurrency, this too continues to fascinate the
majority of the audience. Needless to say, it would be highly useful to keep an eye (and possibly contribute) towards
Mimblewimble [8].

The next talk within the session was given by Ian Miers about ZCash [9]. He walked the audience through the genesis, present
status and the future work on the ZCash. The underlying purpose of ZCash is to provide complete privacy to its users which is something that other cryptocurrency such as Bitcoin has been known to fail in a spectacular fashion. One interesting section of the talk was about the ceremony [10] that is used for the generation of secure parameters. Ian also talked about the regulations but it was quite hard to follow that...

The final talk in this session was based on Zero Knowledge protocol by Steven Goldfeder or to be more precise it was based
on a rather clever attack on Zero Knowledge protocol.

End of the `cryptocurrencies` session brought up the important ceremony of the conference: the `Levchin
prize` [11]. This year
the prize was awarded to Hugo Krawczyk for his contribution to real world cryptographic schemes that has strong security
guarantees to be proven by concrete security proofs. The other prize was given to the entire OpenSSL team for their
improvements to overall code quality of OpenSSL that actively takes into consideration the security aspects. 

The afternoon session started with strong offeree :P It was the `Attacks I` session of the conference. The most
appreciated talk of this session was without a doubt the talk given by Daniel Genkin (University of Penn) about side
channel attacks on implementation of Curve25519. A rare sight of the talk was a real live attack demonstration! 

The second talk of this session given by Ruxandra Olimind, was about the general problem of private identification protocols from cryptographic point of view. The crux of talk was to address the problem of constructing an efficient and scalable secure identification  technique for mobile communication systems.

The final talk of this session was about using Confidential Computing as a means of avoiding side channel attacks by Olya Ohrimenjo (Microsoft).

The final session of the first day was the `Usability and privacy` which started with a talk by Yasemin Acar about Comparing the usability of cryptographic APIs. This was quite an interesting talk as measuring the `usability` of cryptographic API is something  completely new! The study consisted only of Python based cryptographic API which was a bit disappointing but still interesting to see that as many as 256 people finished the given tasks for the study.

The second talk in this session was by Emily Stark (Google) about certificate transparency and its issues with
solutions. It was fascinating talk that covered everything one needs to know about Certificate Transparency. Google had managed to force certificate authorities to comply with the project's requirements completely on its own power!

The third talk of the session was about the security in group chats where a Paul Rosler (University of Bochum) talked about end-to-end security in group chats where an attack in
the popular protocol `Signal` was presented (More general information about this attack check [12]).

The final talk of the session (and the day) was about privacy preserving search using secure computation by Gilad Asharov (Cornell Tech).

## Day 2

Second day of the RWC started with session on `Post-quantum crypto`. The first talk was by Melissa Chase (Microsoft)
    about [Picnic] [13] [14], Microsoft's submission to the post-Quantum cryptography NIST standardization competition.

The second talk of the day was given by Patrick Longa (Microsoft) about Supersingular isogamy based cryptography schemes named SIDH and SIKE. Supersingular isogamy key encapsulation (SIKE) [15] is one of the entry to NIST standardization competition.

The third (and final) talk of this session was not exactly technical but rather an informative talk about research institutes funded in UK for the purpose of Cyber Security. One of them is RISE (Research Institute in Secure Hardware & Embedded Systems) that will focus on the hardware based security (IoT being the forefront of this). One of the numerous projects that is being initiated at the institute is `DeepSecurity` that aims to research for ways to use Deep Learning for security verification of EDA tools with major focus around the issues of Hardware Trojan detection. The website of RISE is still under construction...

The second session of the day was `Broken standards` which began with the famous talk of `Shattered` (the SHA-1 collision)
    by Pierre Karpman. Karpman was part of the group that finally broke the SHA-1 in practice, precisely a year before this talk. He presented how the attack evolved without going into the technical details. Despite its non-technical nature, it was extremely simple and informative talk, especially when it came to explaining the complexity of the attack. Complexity in theory fails to take into consideration the practicality of the attacks, for example, an algorithm that takes 2^60 operations doesn't really reveal much as running it over ASIC, CPU or GPU will produce polarizing results. *Fun fact: The talk ''introduced'' an innovative way of measuring the cost of attack by comparing it with the amount of energy required for water to boil.*

The second talk about the session was by F. Betul Durak about an attack on FF3. They proposed a new generic attack on Feistal networks that is applicable on FF3 standard, on the condition that the message space is small. Furthermore, they propose an easy fix to avoid this attack. One of the most technical talks of the day.

The final (and most anticipated talk of the whole conference) was a special talk by Jon Horn about `Spectre and Meltdown`. Both Spectre and Meltdown had destroyed (in good and bad sense) the Christmas and New Year for security people around the globe. The talk was excellent summary of the attacks and its impacts. For further reading, check [16].

A small `Lightning Talks` session was arranged where participants had just a minute to talk about anything they wished.
     Many talked about open positions at their institutions, companies and general stuffs. Some also presented nice poetry
     about ECC [17].

After lunch the session was `TLS` where the first talk was given by Nick Sullivan(Cloudfare) about pairing and
identity-based broadcast encryption (Heard it for first time as an applied case based on those techniques) that is used in
Cloudfare's Geo Key Manager. Quite interesting talk which was made lively by Sullivan's enthusiasm about the work.

The next talk was based on TLS 1.3 by Thyla van de Merwe (Royal Holloway) which talked
about the change in ecosystem of coding and how it improved the overall security offered by the TLS. 

The final talk of this session was by David Benjamin (Google) who talked about the troubles at maintaining and forcing other to upgrade from
legacy versions of the TLS that are still existing in the wild. This was the most hilarious talk that shows how difficult it was for Benjamin (or Google) to work with buggy servers that used idiotic TLS implementation and settings. *Fun fact: Benjamin described how one vendor who was contacted about changing their buggy servers replied that 'we just wanted to sell customers a box that did something`.*

The final session of the day was about `Crypto in cloud` that began with a talk about trusting encrypted cloud by Anders Dalskov (Aarhus Uni.). The talk focused on building and  assessing the widely used SpiderOak [18] provider and providing an updated threat model for the Encrypted Cloud Storage (ECS) systems. This updated model is concrete enough to be valid even in the presence of passive or active malicious servers. The talk also showed how the security of a real ECS (SpiderOakONE in this case) breaks down in the presence of a malicious server.

The second talk in this session was given by Manish Mehta (Netflix) about how Netflix handles the secrets in the AWS using schemes like puncturable encryption. A new construction was derived to solve the problems at Netflix including the goal of having secrets that must never be viewed in plaintext except by the creator of that secret and the intended consumer. It was interesting talk about how a problem that had theoretical solutions in academia was transformed to make it possible to be applicable for a real world scenario at a large scale.

The final talk of the day was given by people from Facebook about how they succeeded in scaling the backend authentication at Facebook using some innovative Crypto techniques that are supplemented by TLS.

## Day 3

The final day was a half-day conference but packed with quite some nice goodies. The first session of the day was `New Crypto` where the first talk was by Trevor Perrin who talked about his Noise protocol framework. The `Noise Protocol Framework` [19] is one of the most exciting innovations in cryptography in recent years. It is used to build cryptographic protocols that are based on the Diffie-Hellman protocol. The talk was more about the underlying ideas for modern protocol designs and the problems that still exist with them, finally concluding the talk with the goals that Noise aims to achieve. 

The second talk of the session was about bloom filter encryption and its application towards 0-RTT key exchange by David Derler (IAIK, Graz University).

The third talk of the session was about InterMAClib by Martin Albrecht. InterMAClib is a small and simple secure scheme for authentication that is designed to deal with fragmentation of ciphertext in the SSH protocol. This scheme was originally introduced in paper by Kenneth Paterson [20] that was then implemented and tested in real last year that yielded favorable results. If it is understood correctly then despite its positive results it is still in academic prototype stage which may soon be integrated in OpenSSH, hopefully replacing the set of legacy ciphers.

The final talk in this session was by Seny Kamara about building and deploying an encryption search system. The talk focused mostly on Pixek [21] which is application with end-to-end encryption for storing photos on cloud. In this application a user is asked to link the photo with some tag which can be later used to search for photos that are saved in the cloud. This application is currently available only for Android platform with others coming soon. For more information about this application check [22].

The second session for this day was `Attacks II` that started with a solid talk by Junwei Wang (CryptoExperts) about the famous White-Box crypto competition [23]. The competition was similar to CTF (Capture the flag) for which the winners were announced at CHES 2017. Despite having a winning submission, it was broken like all other submissions for the competition. All the submissions that were available for breaking are available online [24].

The second talk was by Kristain Gjosteen (Norwegian University of Science and Technology) about the effects of faulty implementation in pseudo random number generator that caused a provably secure protocol to be highly insecure. The third talk of the session was by Joanne Woodage about analysis of the NIST publication titled 'Recommendation for Random Number Generation using Deterministic Random Bit Generators'. The fourth talk of this session was by Matthew Smith (University of Oxford) about the vulnerability in the aircraft. The exact details about the vulnerability seems a bit sketchy and as with majority of the exploits, the aircraft manufactures do not seem particularly concerned about that... The final talk of this session dealt with random number generation in quantum setting. The talk was given by Julio Hernandez-Castro (University of Kent) that analysed the different quantum random generators that are developed by various entities.

The final session of the conference titled `Verification and provable security` begin with the talk by Jean Paul Degabriele (University of Darmstadt) about tagging attacks on Tor and its severity. It then proposed some adaptations for Tor that would prevent such tagging attacks.

The second talk of the final session was by Douglas Wikstrom (KTH) about mix-net systems that are the main ingredient of electronic voting systems. The talk then introduced the audiences to a spin-off company Verificatum [25].

The final talk of the conference was about HACL* in Mozilla Firefox presented by Benjamin Beurdouche (INRIA). The talk presented the issues in implementing secure and correct cryptographic primitives as a means to solve this issue, the people at INRIA created a verifiable portable C cryptographic library that implements certain cryptographic primitives, named HACL*. The talk provided a nice overview of the challenges that had to be solved when integrating an (almost) academic project in a production ready code. The most interesting point of the project is that it has now been integrated by Mozilla Firefox.

## References

[1] Joux, Antoine. "[Authentication failures in NIST version of
GCM](https://csrc.nist.gov/csrc/media/projects/block-cipher-techniques/documents/bcm/comments/800-38-series-drafts/gcm/joux_comments.pdf)." NIST Comment (2006): 3.

[2] Gueron, Shay, and Yehuda Lindell. "[Better Bounds for Block Cipher Modes of Operation via Nonce-Based Key Derivation.](https://eprint.iacr.org/2017/702.pdf)" (2017).

[3] Online article. "[Google's Gmail problems](https://gmail.googleblog.com/2009/09/todays-gmail-problems.html)".

[4] Github repository. "[CrunchyCrypt](https://github.com/google/crunchy)".

[5] Github repository. "[Keyczar](https://github.com/google/keyczar)".

[6] Github repository. "[Tink](https://github.com/google/tink)".

[7] Poelstra, Andrew. "[2016-10-06 (commit e9f45ec)](http://mimblewimble.cash/20161006-WhitePaperUpdate-e9f45ec.pdf)."

[8] Github repositories. "[Mimblewimble](https://github.com/mimblewimble)".

[9] ZCash: Official website. "[ZCash](https://z.cash)".

[10] Wilcox, Zooko. "[The Design of the Ceremony](https://z.cash/blog/the-design-of-the-ceremony.html)".

[11] Levchin prize, official website. "[`Levchin prize`](http://levchinprize.com)".

[12] Green, Matthew. "[Attack of the Week: Group Messaging in WhatsApp and Signal](https://blog.cryptographyengineering.com/2018/01/10/attack-of-the-week-group-messaging-in-whatsapp-and-signal)."

[13] Chase, Melissa, et al. "[Post-quantum zero-knowledge and signatures from symmetric-key primitives](https://eprint.iacr.org/2017/279.pdf)." Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security. ACM, 2017.

[14] Official Website. "[Picnic](https://microsoft.github.io/Picnic/)". Microsoft Research.

[15] SIKE : Submission for NIST. "[SIKE Zip File](https://csrc.nist.gov/CSRC/media/Projects/Post-Quantum-Cryptography/documents/round-1/submissions/SIKE.zip)". NIST.

[16] Graham-Cumming, John. "[An Explanation of the Meltdown/Spectre Bugs for a Non-Technical Audience](https://blog.cloudflare.com/meltdown-spectre-non-technical/)". Cloudfare Blog.

[17] Youtube Video. "[Lightning talks | Short talks by the participants | RWC 2018](https://youtu.be/o4U0Gfh-0L4?t=15m50s)".

[18] SpiderOakONE Website. "[Personal Cloud Storage for Photos, Musics & Videos | SpiderOak](https://spideroak.com/one/)".

[19] Noise Protocol Framework Website. "[Noise Protocol Framework](noiseprotocol.org)".

[20] Boldyreva, Alexandra, et al. "[Security of symmetric encryption in the presence of ciphertext fragmentation.](https://link.springer.com/content/pdf/10.1007/978-3-642-29011-4_40.pdf)" Annual International Conference on the Theory and Applications of Cryptographic Techniques. Springer, Berlin, Heidelberg, 2012.

[21] Pixek : Official Website "[Pixek](https://pixek.io)".

[22] Greenberg, Andy. "[An App that encrypts your photos from camers to cloud](https://www.wired.com/story/pixek-app-encrypts-photos-from-camera-to-cloud/)". Wired.

[23] WhiBOX Crypto Challenge : Official Website. "[CHES 2017 Challenge](https://whibox.cr.yp.to)".

[24] Github repository. "[Whibox-Context.github.io](https://github.com/whibox-contest/whibox-contest.github.io)".

[25] Verificatum : Official Website. "[Verificatum](www.verificatum.com)".

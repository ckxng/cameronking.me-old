---
layout: page
title: Keysigning
---

<p>I won't ever export signatures to keyservers without first checking with the key owner.  Since there is not a lot of interest in keysigning, I also won't go out of my way to seek signatures.  In fact, at the time of writing this, I don't have any signatures on my own public key... and I have not exported a signature to a keyserver in several years.  I do, however, have a large number of signatures on my local keyring.</p>

<p>Per <a href="http://tools.ietf.org/html/rfc4880">RFC4880</a>, there are four types of key certification signatures.  Here I will describe what my conditions are for validating keys for each kind of signature.</p>

<h2 id="genericcertification">Generic certification</h2>

<pre><code>0x10: Generic certification of a User ID and Public-Key packet.
   The issuer of this certification does not make any particular
   assertion as to how well the certifier has checked that the owner
   of the key is in fact the person described by the User ID.
</code></pre>

<p>Sometimes, it's useful to sign a key that doesn't belong to a person.  Some organizations have things like "package signing keys".  This would mainly show up in my local keyring.</p>

<p>I used to use this for all keysigning, but I tend not to anymore in favor of more detailed assertions as indicated below.</p>

<h2 id="personacertification">Persona certification</h2>

<pre><code>0x11: Persona certification of a User ID and Public-Key packet.
   The issuer of this certification has not done any verification of
   the claim that the owner of this key is the User ID specified.
</code></pre>

<p>I will apply this signature to a key if I obtained it from a fairly trustworthy source (a user's website), but have not received any direct proof that the UID is accurate.  I can't think of any reason I would export such a signature.  This type of signature will only be found in my local keyring.</p>

<h2 id="casualcertification">Casual certification</h2>

<pre><code>0x12: Casual certification of a User ID and Public-Key packet.
   The issuer of this certification has done some casual
   verification of the claim of identity.
</code></pre>

<p>I have verified the key fingerprint and UID by receiving a unique signed message from the email address or username listed in the UID.</p>

<h2 id="positivecertification">Positive certification</h2>

<pre><code>0x13: Positive certification of a User ID and Public-Key packet.
   The issuer of this certification has done substantial
   verification of the claim of identity.
</code></pre>

<p>I have verified the key fingerprint and name portion of the UID using difficult-to-fake government ID or some other highly reputable document.  I may also give this signature if I personally know and trust this user.</p>
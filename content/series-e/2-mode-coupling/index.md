---
title: "How a Brake Squeals — Even When Friction Is Constant"
date: 2026-06-05
math: true
description: "A disc brake can squeal even when the friction coefficient barely changes with speed. A minimal two-degree-of-freedom model shows why: the squeal is not driven by friction that weakens with speed, but by the geometry of the coupling between two springs, which friction makes asymmetric."
summary: "A disc brake squeals even when friction is essentially constant. A minimal two-degree-of-freedom model shows the squeal comes from an asymmetric coupling, not from negative damping."
cover:
  image: "ET2_cover.webp"
  alt: "Isometric illustration of an engineer's desk: a laptop showing a spiralling oscillation, a notebook sketch of a spring–mass–belt model, and a brake disc"
  relative: true
tags: ["Vibrations", "Friction", "Dynamics", "Instability"]
---

A disc brake squeals. You have heard it: a steady, almost pure tone, loud out of all proportion to the gentle pressure of a pad on a rotor. It is one of those everyday noises that turns out to hide a surprisingly deep piece of mechanics.

For a long time the textbook explanation went like this. The friction coefficient $\mu$ between pad and disc drops as the sliding speed rises. When the pad oscillates, it sometimes moves *with* the disc (low relative speed, high $\mu$, large friction force) and sometimes *against* it (high relative speed, low $\mu$, small force). Over one cycle the force does a little more pushing than braking, the oscillation gains a sliver of energy, and it grows. A falling $\mu(v)$ curve acts like negative damping.

It is a clean story, and it is not wrong — that mechanism is real. The trouble is that brakes squeal even when $\mu$ is, for all practical purposes, *constant* with speed. Measure the curve, find it nearly flat, and the brake still sings. So the falling-$\mu$ explanation cannot be the whole picture. Something else is feeding the oscillation.

That "something else" is the subject of a minimal model built by Hoffmann, Fischer, Allgaier and Gaul in 2002. Their model has two degrees of freedom and three springs, and it does something quietly remarkable: it squeals with a perfectly constant $\mu$.

## The reservoir and the tap

Start with the one fact that never changes: a growing oscillation needs a net inflow of energy on every cycle. An amplitude that climbs cycle after cycle is, by definition, being paid into.

Where does the payment come from? Here it helps to separate two questions that are easy to confuse. The disc spins at a constant speed, driven by the car. That sliding is an enormous, effectively bottomless reservoir of energy — it is always there, whether or not anything squeals. So the question is never *whether* there is energy available. The question is what opens the tap: what lets a thin trickle from that reservoir flow, every cycle, into a particular vibration and keep it growing.

The falling-$\mu$ story is one kind of tap. Hoffmann's model is another, and it works without touching $\mu$ at all.

## A model with almost nothing in it

Picture a small block resting on a belt that slides underneath it at constant speed. The block is held by three springs:

- two inclined springs, $k_1$ and $k_2$, anchored above and to the sides;
- one vertical spring, $k_3$, between the block and the belt — this is the stiffness of the contact itself.

The block can move in two directions: $x$, parallel to the belt (call it *in-plane*), and $y$, perpendicular to it (*out-of-plane*). Two degrees of freedom, nothing more.

Now the friction. The belt slides, so it drags the block along $x$ with a friction force. By Coulomb's law that force is proportional to the normal force pressing block and belt together — and the normal force is set by the vertical spring $k_3$, hence by how far the block has moved out-of-plane:

$$F_F = \mu k_3 y$$

Read that equation slowly, because the whole story is in it. The friction force **depends on $y$** (push the block toward the belt, the contact tightens, friction grows) but it **acts along $x$** (it drags the block in the sliding direction). And there is no mirror image: moving the block along $x$ does not change how hard it presses on the belt, so it does not change the normal force. Motion in $y$ feeds a force in $x$; motion in $x$ feeds nothing back.

It is convenient to bundle the two constants that control this effect into a single knob:

$$D = \mu k_3$$

$D$ is the one number we will turn for the rest of the essay. It measures how strongly friction couples the two directions.

## A coupling that only goes one way

Without friction, the springs already couple $x$ and $y$. An inclined spring, stretched in one direction, pulls in both — that is just geometry. Crucially, this structural coupling is **symmetric**: $y$ influences the force on $x$ exactly as much as $x$ influences the force on $y$. Springs are conservative; over any closed path they give back every joule they stored. A symmetric coupling cannot, on its own, pump a vibration.

Friction breaks the symmetry. Its coupling runs in one direction only — $y \to x$, never $x \to y$. Writing the equations of motion for the reference case in Hoffmann's paper (with the masses and stiffnesses scaled to round numbers) makes the asymmetry visible:

$$\ddot{x} = -2x - (1-D)\,y$$
$$\ddot{y} = -x - 2y$$

Look at the coefficient of $y$ in the first equation: $(1-D)$. It is built from two pieces with opposite signs — the structural pull of the springs ($+1$) and the friction drag ($-D$). The coefficient of $x$ in the second equation is just $-1$: structure only, no friction. The two off-diagonal numbers, $(1-D)$ and $-1$, are no longer equal. The stiffness matrix is asymmetric, and that asymmetry is entirely the work of friction.

That single number $(1-D)$ is where everything happens. The rest of the essay is the story of watching it cross zero.

## Try it yourself

Before the explanation, the phenomenon. The tool below is the model, running live. There is one slider that matters — $D$ — and three things worth watching: the orbit the block traces in the $x$–$y$ plane, the force field around it, and the two arrows that fight over the net in-plane force (the green elastic pull, the red friction drag).

Start with $D$ small and watch the block trace a slow, bounded rosette: a *beating* pattern, the amplitude swelling and shrinking but never running away. Now push $D$ up toward 1, and past it. Somewhere around $D = 1$ the rosette stops closing on itself and begins to spiral outward. That outward spiral is the squeal.

<div class="wide-tool">
  <iframe src="/calculators/E2_mode_coupling_explorer.html" title="Mode-Coupling Explorer — Hoffmann (2002)" width="100%" height="1000" style="border:none;" loading="lazy"></iframe>
</div>

Spend a minute with the slider before reading on. The argument below is just a careful account of what you have already seen.

## Three regimes

**Below threshold, $D < 1$ — beating.** The system has two normal modes with two close frequencies. Released from a generic start, it beats: energy sloshes back and forth between the in-plane motion, the out-of-plane motion, and the friction contact. The amplitude pulses, but the books balance. Over one full beat as much energy flows in as flows back out, and the orbit — that rosette — *retraces and cancels* itself. The block always wins back what it lent.

**At threshold, $D = 1$ — the coupling vanishes.** Set $D = 1$ and the coefficient $(1-D)$ becomes exactly zero. The first equation loses its dependence on $y$ altogether:

$$\ddot{x} = -2x \qquad \ddot{y} = -x - 2y$$

The in-plane motion is now deaf to $y$ — but the out-of-plane motion still hears $x$. The coupling has gone one-way in the strongest possible sense: $x$ drives $y$ and gets nothing back. And here is the catch. The $x$ oscillation runs freely at its natural frequency $\sqrt{2}$, and it drives the $y$ equation, whose natural frequency is *also* $\sqrt{2}$. A driver landing exactly on the resonance of what it drives — the $y$ amplitude climbs, not exponentially yet, but *linearly* in time. (The mechanism is ordinary forced resonance.) This is instability taking its first breath: weak, linear, but unmistakably no longer bounded.

**Above threshold, $D > 1$ — squeal.** Now $(1-D)$ turns negative. The orbit no longer retraces itself; it spirals outward, each loop a little wider than the last, and the area it sweeps accumulates with the same sign turn after turn. The amplitude grows like $e^{\sigma t}$ with $\sigma > 0$, and it never stops on its own.

One detail is worth pinning down, because it is the thing people most often get backwards. It is the **amplitude** that grows, not the frequency. As $D$ approaches 1 the two natural frequencies do not separate — they *merge*, into the single value $\sqrt{2}$. Beyond threshold the system rings at that one fixed frequency, and rings louder and louder. The pitch of a squeal is steady; only its loudness runs away.

## The sign change, from three sides

The whole phenomenon turns on $(1-D)$ passing through zero. It is worth looking at that one event from three different angles, because they are the same fact wearing three costumes — and seeing them line up is the payoff of the model.

**As eigenvalues.** Propose oscillating solutions $e^{st}$ and the system collapses to a single equation,

$$s^2 = -2 \pm \sqrt{1-D}$$

Everything hangs on the term under the root. For $D < 1$ it is real, $s^2$ is real and negative, $s$ is purely imaginary — pure oscillation, $\sigma = 0$. For $D > 1$ the quantity under the root goes negative, $s^2$ becomes *complex*, and a complex $s^2$ forces $s$ to have a real part. One of the two values gives $\sigma > 0$: growth. The crossing of zero by $(1-D)$ is the crossing from real to complex.

**As forces.** In the explorer, the net in-plane force is the contest between two arrows: the green elastic pull (always trying to restore) and the red friction drag (growing with $D$). Below threshold the green wins and the resultant points back toward home — a restoring force. At $D = 1$ they cancel. Above threshold the red arrow overtakes the green, and the resultant flips: what used to pull the block back now shoves it further out. A restoring force has become a propelling one.

**As energy.** The only force that can do net work over a cycle is friction, and its work is $W = D \oint y\,dx$ — proportional to the *signed area* of the orbit in the $x$–$y$ plane. A straight-line orbit encloses no area and does no net work. An open, looping orbit encloses area, and the sign of that area — the direction the block goes around — decides whether friction feeds the motion or drains it. Below threshold the orbit retraces and the areas cancel; above threshold the spiral lays down loop after loop of the same sign, and the work piles up. (This area reading is our own lens — equivalent to Hoffmann's energy argument, but not in his paper.)

Three descriptions, one event. The real part of an eigenvalue turning positive; a restoring arrow flipping to a pushing one; the signed area of an orbit starting to accumulate. They happen at the same value of $D$ because they are the same thing.

And here is what makes the model worth the trouble. None of this needed $\mu$ to change with speed. There is no $\mu(v)$ in any of these equations, no negative damping, no special friction law. There is a constant $\mu$, a one-way coupling, and a geometry that friction renders asymmetric. That asymmetry, all by itself, is enough to open the tap.

## Where this leaves us

So the surprising part of a squeal is not that energy is available — the sliding disc sees to that. It is that a perfectly ordinary, constant friction, acting through an asymmetric coupling, is enough to let that energy in. Turn one knob, $D$, past the point where the friction drag overtakes the elastic pull, and a bounded beating becomes an unbounded spiral. The brake sings, and it sings at a single, fixed, coalesced frequency, with nothing in the model fading or weakening with speed.

That is where we stop. There is more to the story — what happens when you add damping turns out to be stranger than you would guess, and not always for the better — but that is a separate puzzle for another essay. Here the arc is clean: a constant force, an asymmetric geometry, and a sign that changes.

---

## Reference

Hoffmann N., Fischer M., Allgaier R., Gaul L., *A minimal model for studying properties of the mode-coupling type instability in friction induced oscillations*, Mechanics Research Communications, 29 (2002), 197–205.

*This essay presents an engineering interpretation of the cited work. It is not a reproduction of the original paper. For the complete derivation, consult the original publication.*

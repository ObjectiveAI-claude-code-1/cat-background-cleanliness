# cat-background-cleanliness

Scores how clean and non-distracting the background is in a cat photograph, evaluating whether the cat stands out clearly as the subject or gets lost in a visual crowd of competing elements.

## Overview

The difference between a captivating cat photograph and a forgettable one often has nothing to do with the cat itself. The same cat, in the same pose, can produce two entirely different photographs depending on what surrounds it. `cat-background-cleanliness` evaluates the relationship between the cat and its surroundings, producing a scalar score from **0** (cluttered, chaotic background that overwhelms the subject) to **1** (clean, supportive background that lets the cat shine).

A high score does not demand an empty or sterile background. A bookshelf, a garden, or a kitchen counter can serve beautifully — what matters is that the background remains visually secondary to the cat.

## Input

| Field | Type | Required | Description |
|---|---|---|---|
| `cat_photo` | `image` | Yes | A photograph containing a cat to be evaluated for background cleanliness. |

The function accepts a single image — one photograph, examined in full. It may be a carefully composed portrait or a casual phone snapshot. The function does not evaluate camera quality, lighting technique, or the cat itself. It evaluates only the relationship between the cat and the space around it.

## Output

A scalar score in the range **[0, 1]**:

| Score Range | Interpretation |
|---|---|
| **0.8 – 1.0** | Excellent — the background is clean and fully subordinate to the cat. The viewer's eye settles on the subject naturally and without effort. |
| **0.5 – 0.8** | Moderate — the cat is recognizable as the subject, but some background elements draw attention or introduce mild visual competition. |
| **0.2 – 0.5** | Poor — the background competes significantly with the cat. Multiple distractions or a disorganized space make it difficult to focus on the subject. |
| **0.0 – 0.2** | Very poor — the cat is lost in a cluttered, chaotic visual field. The background overwhelms the subject entirely. |

## What It Evaluates

The function assesses background cleanliness through three distinct qualities:

### 1. Visual Hierarchy

Does the cat command the viewer's attention as the clear, dominant subject? This quality evaluates the power relationship between the cat and its surroundings — whether the background stays subordinate through calm tones, muted colors, and unassuming textures, or asserts itself through bold patterns, vivid colors, and eye-catching elements that rival the cat for visual prominence. A cat can be small in the frame and still dominate the image if the background is calm and recessive. Conversely, a cat can fill most of the frame and still feel secondary if the background is visually aggressive.

### 2. Distraction Density

How many specific competing elements are present in the background that fracture the viewer's focus? This quality identifies and counts individual visual interruptions: scattered household objects, bright signage, bold geometric patterns, glowing screens, cluttered surfaces, and especially other animals — which are uniquely powerful distractions because they are subjects in their own right. Distractions are evaluated both by their number and their cumulative impact. A single coffee mug may be forgiven; a coffee mug next to a stack of mail, a phone charger, and a half-eaten plate of food transforms the background from a backdrop into an inventory of visual noise.

### 3. Spatial Harmony

Does the surrounding space cohere into a calm, ordered, unified visual field, or does it feel chaotic, fragmented, and restless? A background can have relatively few individual distractions and still feel disorganized if its elements share no visual relationship — tangled cables, furniture at odd angles, mismatched textures colliding without rhythm. Conversely, a background with some content can feel deeply harmonious if its elements belong together naturally, like a garden or a tidy kitchen counter. This quality captures the emotional register of the space: does it feel settled and calm, or does it create visual anxiety? Cleanliness is not the absence of content — it is the presence of order.

## What It Penalizes

- **Scattered objects** — household clutter, toys, papers, cables, and miscellaneous items strewn around the cat
- **Bold patterns** — loud wallpaper, geometric rugs, or patterned fabrics that compete with the subject
- **Bright signage** — text, logos, or brightly colored markers that pull the eye
- **Other animals** — a second cat, a dog, a bird, or any living creature that creates competition for the viewer's attention
- **Visual chaos** — a general tangle of visual information where unrelated elements collide without cohesion
- **Visually assertive backgrounds** — any background that rises to or surpasses the cat in visual weight

## What It Rewards

- **Subordinate backgrounds** — spaces that exist with texture and character but do not assert themselves
- **Visual calm** — muted tones, soft textures, and unassuming colors that let the cat stand out
- **Cohesive environments** — backgrounds whose elements relate to one another naturally (a garden, a clean windowsill, a tidy shelf)
- **Clear subject isolation** — compositions where the viewer's eye lands on the cat immediately and stays there

## Use-Cases

- **Content curation** — Filter and rank cat photograph submissions for websites, social media accounts, or photography collections by surfacing images where the cat truly shines and flagging those undermined by cluttered backgrounds.
- **Photography feedback** — Provide cat owners with actionable feedback on their photographs, helping them understand that the environment — not the cat — may be undermining their images.
- **Dataset quality** — Score and prioritize training images for machine learning pipelines, filtering out photographs where visual noise makes it difficult to isolate the subject from the scene.
- **Automated quality gates** — Set minimum background cleanliness thresholds for platforms that accept user-submitted cat photography.
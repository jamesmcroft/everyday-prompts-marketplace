# Content Creator Cookbook

Practical workflows and real-world examples for the `content-creator` plugin. These scenarios show how to use skills individually and how the agents chain them together for end-to-end content production.

## Getting Started

```
/plugin marketplace add jamesmcroft/everyday-prompts-marketplace
/plugin install content-creator@everyday-prompts-marketplace
```

Once installed, invoke the `@content-creator` agent as your starting point. It classifies what you need and routes to the right skill or agent.

---

## Workflow 1: Write and Launch a Blog Post

**Scenario:** You have a topic and want to go from idea to published article with cross-platform promotion.

**What to say:**

> Write a blog post about how small teams can adopt continuous discovery practices, then promote it across my channels.

**What happens:**

1. The `@content-creator` coordinator recognizes this as a write-and-launch workflow.
2. It hands off to `@article-writer`, which:
   - Asks you to confirm the audience, keyphrase, and tone.
   - Researches the topic for current facts and sources.
   - Produces an outline for your approval.
   - Drafts each section with checkpoints.
   - Self-reviews for readability and accuracy.
   - Delivers the article with SEO metadata.
3. Once the article is ready, the coordinator kicks off the Content Launch workflow:
   - Proposes a platform plan (LinkedIn, X, Instagram, Pinterest, newsletter).
   - You confirm which platforms.
   - It produces each piece sequentially: promotional posts, carousel plan, reel script, pin descriptions, newsletter draft.
   - Delivers the full package with a suggested publishing schedule.

**Time saved:** Instead of writing the article, then separately crafting 5-6 promotional pieces, the launch workflow produces everything from the same source material in one session.

---

## Workflow 2: Plan a Week of Content

**Scenario:** It's Monday and you need to plan what to publish across all platforms this week.

**What to say:**

> Plan my content for this week. I post on my blog once, Instagram 3 times, TikTok twice, and send a newsletter on Thursday. My niche is sustainable living for urban professionals.

**What happens:**

The `/content-calendar` skill builds a structured week:

- Assigns topics to each publishing slot.
- Flags where one piece of content can feed multiple platforms (e.g., Tuesday's blog post becomes Wednesday's carousel and Thursday's newsletter feature).
- Balances variety across the week.

**Follow-up:** After the calendar is set, you can say "write Tuesday's blog post" and the coordinator routes to `@article-writer` with the topic already loaded.

---

## Workflow 3: Brainstorm Fresh Topics

**Scenario:** You're running dry on ideas and need inspiration grounded in your niche.

**What to say:**

> Help me brainstorm content ideas. My audience is frontend developers interested in design systems. I've recently covered component libraries and token-based theming.

**What happens:**

The `/content-ideation` skill:

- Researches current trends in your niche.
- Identifies audience questions you haven't covered.
- Produces 10 ideas ranked by potential, each with a title, angle, best platform, and format.
- Flags which ideas build on your existing content vs. break new ground.

---

## Workflow 4: Turn One Article into Everything

**Scenario:** You published a blog post yesterday. Now you want to squeeze maximum value from it.

**What to say:**

> I just published this article: [URL]. Repurpose it for Instagram, TikTok, Pinterest, and my newsletter.

**What happens:**

The `/content-repurpose` skill:

- Reads the article and extracts the key message, supporting points, strongest hook, and quotable moments.
- Produces platform-native versions:
  - **Instagram carousel:** 8-slide plan with copy per slide.
  - **TikTok script:** 30-second hook-value-CTA structure.
  - **Pinterest:** 3 pin descriptions with different angles.
  - **Newsletter segment:** teaser with personal angle and CTA.

Each version gets a different hook. None are copy-paste.

---

## Workflow 5: Plan and Script a Reel

**Scenario:** You want to create a TikTok about a topic you know well but need the pre-production plan.

**What to say:**

> Plan a TikTok about the 3 biggest mistakes people make when starting a vegetable garden.

**What happens:**

The `@video-planner` agent:

1. Generates 3-5 hook options for the first 3 seconds.
2. You pick the hook.
3. It produces a shot-by-shot script with timestamps, visual cues, audio/script, and text overlays.
4. Writes an Instagram caption.
5. Generates a cover image prompt.

You walk away with everything you need to hit record.

---

## Workflow 6: Create an Instagram Carousel

**Scenario:** You want to turn a set of tips into a saveable, shareable carousel post.

**What to say:**

> Create a carousel about 5 things every new homeowner should know about energy efficiency.

**What happens:**

The `@carousel-planner` agent:

1. Defines the transformation (what should the reader know after swiping?).
2. Produces slide-by-slide copy: hook slide, context, 5 tip slides, summary, CTA.
3. Writes the Instagram caption.
4. Suggests repurpose opportunities (TikTok, Pinterest, blog FAQ section).

---

## Workflow 7: Generate an Image for Your Post

**Scenario:** Your article is ready and you need a hero image.

**What to say:**

> Create an image prompt for a blog post about remote team collaboration tools. It's for a blog hero image.

**What happens:**

The `/image-prompt` skill produces 3 creative variants:

- **Variant A** (photographic): specific camera, film stock, and shooting conditions.
- **Variant B** (illustrated): an art movement or graphic style.
- **Variant C** (applied format): editorial page, poster, or infographic.

Each is a flowing paragraph you can paste directly into ChatGPT, Midjourney, or DALL-E. Aspect ratio matches the blog hero format (16:9).

---

## Workflow 8: Review a Draft Before Publishing

**Scenario:** You've written a draft and want feedback before it goes live.

**What to say:**

> Review this article for readability. My audience is non-technical product managers.

Then paste or provide the draft.

**What happens:**

The `/readability-review` skill evaluates clarity, flow, impact, conciseness, and engagement for your stated audience. It returns specific, actionable suggestions, not vague "could be improved" notes.

**Follow up with:**

> Now check it for accuracy.

The `/accuracy-review` skill fact-checks claims, flags outdated information, and notes anything that needs independent verification.

---

## Tips

- **Start with `@content-creator`** rather than invoking individual skills. The coordinator knows how to chain workflows and pass context between steps.
- **The Content Launch workflow** is the highest-value flow. Write one strong piece, then let it produce everything else.
- **Image prompts produce 3 variants** with different creative directions. Pick one, combine elements, or ask for more.
- **Repurposing is not copy-pasting.** Each platform gets a different hook and format. The `/content-repurpose` skill handles this automatically.

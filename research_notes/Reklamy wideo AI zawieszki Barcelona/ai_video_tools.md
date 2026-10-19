# AI video tools and production workflows for realistic small-jewelry ads (Vellano Jubiler crest pendants) — state as of 19 Oct 2026

Scope note: "HF-MCP" below means a live, read-only query of the owner's Higgsfield account through the Higgsfield MCP tools on 2026-10-19 (models_explore, get_presets, get_workflow_instructions/bundle files, list_voices, and generate_* with `get_cost:true`). No job was submitted and no credits were spent. All credit prices are for 9:16 and one variant unless noted. WebFetch and curl were blocked by the session proxy for every external site tried (higgsfield.ai, orcarouter.ai, invideo.io), so the external findings come from search-result summaries, not full-page reads. Treat exact third-party numbers as "reported by" and not verified. "Brief" means facts the owner gave in the assignment (past results in this project). They are not independently sourced.

## 1. Which Higgsfield models and features exist now (start/end frames, Marketing Studio, UGC/avatars, lip-sync, motion transfer, virality, TikTok), and what do they cost?

### Takeaway
The Higgsfield catalog has 57 video models and tools. Several cheap models accept a start and an end frame: Kling 3.0 / Kling 3.0 Omni Frames (about 6–9 credits per 5 s), MiniMax H3 at 2K (10 credits per 5 s), Hailuo 2.3 (6 credits per 6 s), Veo 3.1 Lite (12 credits per 8 s) and Wan 3.0 (8.75 credits per 5 s). The account also has motion transfer (Kling 3.0 Motion Control at 17–27 credits per 10 s, plus Genjutsu), Sync Lipsync 3 (54 credits per 15 s), video dubbing into Polish (45 credits per 15 s), Marketing Studio V2 UGC (105 credits per 15 s at 720p), a Virality Predictor and TikTok publishing tools. Seedance 2.5 is the most capable model (30 s clips, references, native audio, region edit), but it is also the most expensive: about 7 credits/s at 720p and 16 credits/s at 1080p. With 937 credits, Seedance 2.5 should only be used for final shots.

### Cited Findings
**Catalog facts (HF-MCP `models_explore list type=video`, 57 items)**
- **Start + end frame (`start_image` + `end_image`) supported by:** `kling3_0` (Kling v3.0: "Multi-shot, audio sync, motion transfer"; std/pro/4k; sound on/off; 3–15 s; 16:9, 9:16, 1:1), `kling_o3_flf` (Kling 3.0 Omni Frames; multi_shots + multi_prompt), `minimax_h3` (2K only, 4–15 s), `minimax_h3_max` (480p/768p), `minimax_hailuo` (variants minimax-2.3 / 2.3-fast; 6 or 10 s; tags "physics, emotion, facial, realistic"), `seedance1_5`, `seedance_2_0`, `seedance_2_0_mini`, `seedance_2_5`, `veo3_1_lite`, `wan2_7`, `wan3_0`, `wan3_0_prime`, `gemini_omni_flash_1_1`, `flux_3_video`, `cinematic_studio_3_0`, `cinematic_studio_video_v2`, `cinematic_studio_video_3_5`, `cinematic_studio_video_4_0`, and `marketing_studio_video` — [HF-MCP models_explore](https://higgsfield.ai)
- **Start frame only (no end frame):** `grok_video_v15_lite` (1–15 s; "1080p is upscaled from 720p"), `grok_video_v15` (2–15 s, also image and audio references), `kling2_6`, `kling3_0_turbo`, `veo3`, `veo3_1` (4/6/8 s; quality basic/high/ultra; variant preview/fast), `happy_horse_video` — [HF-MCP models_explore](https://higgsfield.ai)
- **Reference-image (product/identity) models:** `kling_o3_image_reference` (Kling 3.0 Omni, "up to seven reference images"), `seedance_2_0` ("consistent identity, multi-SKU, e-commerce"), `seedance_2_5` (modes `t2v`, `omni_reference`, `video_edit`, `video_extension`; 4–30 s; `draft` 480p that "can be finalized within seven days" via `draft_job_id`), `minimax_h3`, `wan3_0`, `gemini_omni_flash_1_1` (also has an `edit` mode) — [HF-MCP models_explore](https://higgsfield.ai)
- **Motion transfer / recast:** `kling3_0_motion_control` (image_references + video_references; std/pro; `background_source` input_image or input_video), the `motion_control` tool ("Animate an existing character image with the motion and camera movement from a reference video using Kling 3.0 Motion Control"; 720p/1080p; scene_control image/video), and Genjutsu `hf_mult_motion_control` ("Transfer motion from a reference video to subjects in reference images", 480p/720p/1080p) — [HF-MCP models_explore + motion_control schema](https://higgsfield.ai)
- **Object or person replacement in an existing video:** `hf_mult_replace_object` (Genjutsu: "Replace objects in a source video using reference images"), `ad_multiplier` (edit people, products, backgrounds and so on in a supplied 4–30 s video "while preserving source motion, framing, cuts, timing… default audio"; powered by Seedance 2.5), `ad_multiplier_v2` (Recreate: re-shoot a 4–30 s ad "for another audience, language, product, cast or setting", or regenerate only its hook or CTA), `kling_video_edit` (Kling 3.0 Omni Edit, text + reference images), `marketing_studio_v2_reference2video` ("Recreate a reference video with your own character and product"; input_video, character_image, product_image) — [HF-MCP models_explore + workflow catalog](https://higgsfield.ai)
- **Lip-sync / voice:** `sync_so` = "Sync Lipsync 3" (input_video + input_audio; sync_mode bounce/loop/cut_off/silence/remap); `dubbing` (target_language list includes **`pol`**, plus eng, deu, spa, rus and others); `voice_change`; TTS models `seed_audio` (ByteDance; can clone from audio_references), `text2speech_v2` (variant elevenlabs|minimax|seed_speech|vibe_voice|cozy_voice), `elevenlabs_v4` and `elevenlabs_v4_turbo` (dialogue up to 10 voices / 10,000 chars), `qwen_audio_tts` (its language hints do not include Polish). `inworld_text_to_speech` has Polish voices ("Szymon (pl)", "Wojciech (pl)"), but it is flagged "Game pipeline only" — [HF-MCP models_explore type=audio](https://higgsfield.ai)
- `list_voices` returns more than 120 preset voices (Grady, Ainsley… Vlad, Elena…) with no language metadata. Custom or cloned voices are created with `create_voice` — [HF-MCP list_voices](https://higgsfield.ai)
- **Marketing Studio V2 (`marketing_studio_v2_video`):** types `2d_motion, hypermotion, mixed_media, saas_motion, ugc, video_mode, ugc_v2, product_link, ad_reference, app_video`. `ugc` accepts `product_description`, `user_context` and `delivery_specs` (duration, mode, **language**, call_to_action, format). Product images max 6. Duration 4–30 s. Hooks/settings are supported only for the UGC, Tutorial, Unboxing, Product Review and UGC Virtual Try On presets (per the `marketing_studio_video` param docs) — [HF-MCP models_explore](https://higgsfield.ai)
- The Marketing Studio widget tabs are all / ugc / product-shot / motion / ads / posters / marketplace. The motion catalog holds **231 presets** (types hypermotion, mixed_media, 2d_motion, saas_motion; for example "Fashion Editorial Reveal", "Slow ambient", "Green Tea Macro"). Searching marketing_studio for "jewelry" and viral for "necklace" returned **0 presets** — [HF-MCP get_presets](https://higgsfield.ai)
- **Genjutsu trending motion-transfer presets** include "Unboxed Item Swap", "Rug Transition Swap", "Ceiling Fan Transition", "Cash Stack Recast" and "Parking Lot Recast". Each is a driving video to which you apply your own reference image — [HF-MCP get_presets source=genjutsu](https://higgsfield.ai)
- **Higgsfield's own bundled UGC workflow** (`ugc-video`, formats review / product / unboxing / try-on / tutorial / website) works in four steps: a GPT Image 2 "board" (21:9 sheet with four 9:16 slots), then Seedream 5 Pro cleanup, then visual inspection, then `seedance_2_5` in `omni_reference` mode at 1080p with `generate_audio:true` for native speech ("Do not add a separate narration/TTS job"). The default speech is "English … American accent unless explicitly changed". The workflow forbids fabricated "personal use, endorsements, results… or reviews" and excludes testimonials. Its product intake warns: "If the photo shows a big readable logo, warn the user once (wordmarks render as gibberish or as a real competitor brand)" — [HF-MCP get_workflow_instructions ugc-video + bundle files](https://higgsfield.ai)
- Other bundled workflows: `ad-multiplier`, `ads-studio` (static Meta ads), `product-photoshoot` (packshots, lifestyle, product-with-person closeups), `video-montage` (assembly + Polish/any captions), `video-editing`, `character-sheet`, `narration` ("put me in this video" presenter compositing) — [HF-MCP get_workflow_instructions](https://higgsfield.ai)
- **Virality Predictor:** the `virality_predictor` tool analyzes a confirmed uploaded or generated video ("virality potential, engagement, attention, audience response, retention risk, hook strength") and opens a dashboard. It has no get_cost preflight — [HF-MCP tool schema](https://higgsfield.ai). A third-party blog reports it launched 9 May 2026, accepts clips up to 15 s, and returns a virality score, hook score, hold rate and a "brain heatmap" — [pasqualepillitteri.it](https://pasqualepillitteri.it/en/news/2273/higgsfield-virality-predictor-hook-score-hold-rate-2026). A French review questions how convincing its "neuroforecasting" basis is — [Journal du Net](https://www.journaldunet.com/intelligence-artificielle/1550901-test-complet-de-higgsfield-le-hugging-face-de-l-ia-pour-la-video/)
- **TikTok:** the Higgsfield MCP exposes `tiktok_connect`, `tiktok_accounts`, `tiktok_prepare_publish`, `tiktok_publish_status`, `tiktok_music_trending` and `tiktok_music_tune` (tool names seen in the session's tool list; not called) — [HF-MCP tool list](https://higgsfield.ai)
- **AI influencer / avatar:** `ai_influencer_prepare` (returns design and price without generating) and `ai_influencer_generate`. `soul_2` handles portraits/UGC, and `show_characters(action='train')` trains a reusable Soul ID from 5–20 photos (about 10 min) — [HF-MCP tool descriptions](https://higgsfield.ai)
- **Seedance 2.5 launch:** Higgsfield blog dated 6 Aug 2026 (design-offset says 7 Aug). Clips up to 30 s with sound generated in the same pass, up to 50 references, and "region-level" edits ("point at the object or the face, fix just that") — [Higgsfield blog via search](https://higgsfield.ai/blog/seedance-2-5-on-higgsfield-2026); [design-offset](https://design-offset.com/higgsfield-bytedance-seedance-2-5/). A limited-time unlimited campaign was reported for some plans — [design-offset](https://design-offset.com/higgsfield-bytedance-seedance-2-5/). This account currently shows `unlim.available:false` — [HF-MCP](https://higgsfield.ai)
- Seedance 2.0 `std` mode "requires a Plus plan or higher". The owner is on Plus, so it is available — [HF-MCP models_explore](https://higgsfield.ai)
- **Sora is not in the Higgsfield catalog.** OpenAI shut the Sora app on 26 Apr 2026 and the Sora 2 API on 24 Sep 2026, with no successor listed — [TechJack Solutions](https://techjacksolutions.com/ai-brief/openai-videos-api-sora-2-deprecated-september-2026/); [Zilliz FAQ](https://zilliz.com/ai-faq/what-is-the-sora-shutdown-timeline)

**Price preflights (HF-MCP `get_cost:true`, 2026-10-19, 9:16)** — [HF-MCP generate_video/image/audio get_cost](https://higgsfield.ai)

| Model / setting | Credits | Per second |
|---|---|---|
| grok_video_v15_lite 720p 3 s | 3 | 1.0 |
| grok_video_v15 720p 5 s | 22.5 | 4.5 |
| seedance_2_0_mini 720p 5 s, no audio | 5 | 1.0 |
| kling_o3_image_reference std 5 s, sound off | 5 | 1.0 |
| minimax_hailuo 2.3, 768p, 6 s | 6 | 1.0 |
| kling_o3_flf (Omni Frames) **pro** 5 s, sound off | 6.25 | 1.25 |
| kling3_0 std 5 s, sound off | 7.5 | 1.5 |
| kling3_0_turbo 720p 5 s | 7.5 | 1.5 |
| kling3_0 pro 5 s, sound off | 8.75 | 1.75 |
| wan3_0 720p 5 s, no audio | 8.75 | 1.75 |
| minimax_h3 **2K** 5 s | 10 | 2.0 |
| veo3_1_lite 8 s, no audio | 12 | 1.5 |
| kling3_0 pro 5 s, sound on | 12.5 | 2.5 |
| seedance_2_0 fast 720p 5 s, no audio | 12.5 | 2.5 |
| wan3_0 1080p 5 s, with audio | 17.5 | 3.5 |
| kling3_0_motion_control std 10 s | 17 | 1.7 |
| gemini_omni_flash_1_1 720p 8 s | 24 | 3.0 |
| seedance_2_5 **480p draft** 8 s | 24 | 3.0 |
| kling3_0 pro 10 s, sound on | 25 | 2.5 |
| kling3_0_motion_control pro 10 s | 27 | 2.7 |
| veo3_1 basic/fast 8 s | 32 | 4.0 |
| seedance_2_5 720p 5 s, no audio | 35 | 7.0 |
| cinematic_studio_video_4_0 720p 5 s | 35 | 7.0 |
| dubbing (any target incl. Polish) 15 s | 45 | 3.0 |
| sync_so (Lipsync 3) 15 s | 54 | 3.6 |
| seedance_2_5 720p 8 s, with audio | 56 | 7.0 (audio adds nothing) |
| seedance_2_0 std 1080p 5 s | 60 | 12.0 |
| marketing_studio_video 720p 15 s | 75 | 5.0 |
| veo3_1 high/preview 8 s | 80 | 10.0 |
| marketing_studio_v2_video ugc_v2 720p 15 s | 105 | 7.0 |
| seedance_2_5 **1080p** 8 s | 128 | 16.0 |
| gpt_image_2_5 quality high (1k default) | 1.5 | — |
| gpt_image_2_5 **xhigh 2k** | 4.5 | — |
| nano_banana_pro (default) | 2 | — |
| soul_2 2k | 1 shown (0.12 exact) | — |
| seed_audio, one short Polish sentence | 0.5 | — |

- The owner's past prices from the brief (Grok 1.5 Lite 3 credits per 3 s; Kling 3.0 7.5 std / 8.75 pro per 5 s; gpt_image_2_5 xhigh 2K 4.5; Seedance 2.5 1080p 8 s 128) **all re-confirmed identically** on 2026-10-19 — [HF-MCP get_cost](https://higgsfield.ai)
- `hf_mult_motion_control` and `hf_mult_replace_object` cannot be priced without uploaded media (the preflight returned "missing_roles: image, video") — [HF-MCP](https://higgsfield.ai)

### Inferences
- Seedance 2.5 at 720p costs the same per second with or without audio (35 credits for 5 s silent, 56 for 8 s with audio, both 7/s). If it is used at all, keep `generate_audio:true`. Use 480p draft mode (3/s) to test motion, then finalize only the winner.
- Marketing Studio V2 UGC at 720p for 15 s costs 105 credits, exactly the Seedance 2.5 720p rate. This suggests it runs on Seedance 2.5, consistent with the bundled UGC workflow locking `seedance_2_5`.
- For crest-sensitive shots, the cheap tier is enough for iteration: Kling O3 Frames pro at 6.25, MiniMax H3 at 2K for 10, Hailuo 2.3 at 6, and Grok Lite at 1/s. The 937 credits buy about 150 Kling-class 5 s attempts, or about 7 Seedance 2.5 1080p 8 s finals.
- MiniMax H3 deserves a test. It outputs native 2K, accepts start + end frames, costs 10 credits per 5 s, and is near the top of the October 2026 image-to-video leaderboard (see Q2). Higher resolution should help tiny rhinestones.
- The Kling O3 Frames pro price (6.25) is below Kling 3.0 std (7.5). This may be a promotion or a pricing quirk; re-check with get_cost before each batch.

### Gaps
- Cost of Genjutsu motion-transfer / replace-object and of the Virality Predictor (no preflight without media).
- Whether Marketing Studio V2 `ugc` with `delivery_specs.language` actually supports Polish (the field exists; the allowed values were not listed).
- Whether `dubbing` keeps lip-sync (the tool only lists target languages).

## 2. Which models do independent comparisons rate best in 2026 for realistic humans and hands, metal/jewelry reflections and fine product detail?

### Takeaway
No independent benchmark tests jewelry, logos or hands specifically. On the general Artificial Analysis image-to-video board (with audio), the top six models were within about 20 Elo of each other as of 10 Oct 2026: MiniMax H3 Max, MiniMax H3, Vidu Q4, Gemini Omni Flash, Seedance 2.0 and HiDream. Comparison blogs favor Seedance 2.0 for character consistency, Kling 3.0 (Turbo) for a locked-off, stable product, and Veo 3.1 for photorealism. Sora 2 is discontinued. Model choice matters less than workflow for the crest; see Q3.

### Cited Findings
- Artificial Analysis image-to-video **with audio** leaderboard snapshot of 10 Oct 2026: MiniMax H3 Max 1,195 ±9; MiniMax H3 1,181; Vidu Q4 Preview 1,179; Gemini Omni Flash 1,178; Dreamina Seedance 2.0 720p 1,176; HiDream-O1-Video-1.0 1,175. The top six sit within 20 Elo with confidence intervals of 7–10 points, which is effectively a tie — [OrcaRouter blog (via search summary)](https://www.orcarouter.ai/blog/hidream-o1-video-1-0-leaderboard-debut-api-gap)
- An earlier, undated snapshot had Gemini Omni Flash #1 (1200), Seedance 2.0 720p #2 (1199) and grok-imagine-video-1.5-preview #3 (1118) — [benchmarklist](https://benchmarklist.com/arenas/artificial_analysis_image_to_video/). Scores do not transfer between Artificial Analysis tiers, and third-party figures conflict (Techsy gave Seedance 2.0 1,344 in June 2026) — [Techsy](https://techsy.io/en/blog/best-ai-video-models)
- In a perfume-bottle product test, Kling 3.0 Turbo was the model "closest to a locked-off product camera, bottle rock solid" (Veo 3.1 Fast and Seedance 2.0 Mini moved more) — [Vidlux](https://vidlux.ai/blog/veo-vs-kling-vs-seedance)
- Character/multi-shot consistency: Seedance 2.0 9/10, Kling 3.0 8/10, Veo 3.1 7/10 — [AI Journal](https://aijourn.com/seedance-2-0-vs-kling-3-0-vs-veo-3-1-ai-video-benchmark-test-for-2026/). Kling 3.0 is "second in most write-ups", and Veo 3.1 offers "less reference control" — [Elser.ai](https://www.elser.ai/blog/kling-3-vs-seedance-2-vs-veo-3-1-character-consistency)
- Veo 3.1 was the photorealism pick in one roundup, and Seedance 2.0 was credited with physics — [imgveo](https://imgveo.com/compare/veo-3-vs-kling-3-vs-seedance-2)
- Hands: the only hand-specific claim found is that Seedance 2.0 "loses fine hand detail in close-ups after frame 60 in 40% of cases". It comes with no methodology and is unverified — [Flixly](https://www.flixly.ai/blog/seedance-2-0-vs-kling-3-0-vs-veo-3-1-2026-comparison)
- A creator guide says Kling 3.0 handles realistic human motion and close-ups, while Veo 3.1 suits wide establishing shots — [Atlabs](https://www.atlabs.ai/blog/how-to-make-ai-videos-look-less-artificial-in-2026-(step-by-step-guide))
- Kling 3.0's motion-control release improves identity under occlusion: "partial blockages like accessories or hands no longer disrupt character recognition" — [ComfyUI.org](https://www.comfyui.org/en/kling-30-motion-control-in-comfyui)
- Jewelry-specific failure modes named by a vendor FAQ (updated 1 Aug 2026): "plastic metal sheen, dead gemstones, melted prongs, shadow or color drift". Its suggested image pipeline is to build the aesthetic with GPT-Image-2, lock the exact piece with Nano Banana, and check close, mid and wide shots — [invideo FAQ](https://invideo.io/faq/how-do-you-fix-ai-generated-jewelry-that-looks-fake-or/); [invideo jewelry workflow](https://invideo.io/faq/best-ai-workflow-for-jewelry-ad-image-generation-with/)
- Sora 2 (and sora-2-pro) was removed from the API on 24 Sep 2026. Commentators suggest Veo 3.1 or Kling 3.0 as replacements, and Runway Gen-4.5 for editing-led work — [TechJack Solutions](https://techjacksolutions.com/ai-brief/openai-videos-api-sora-2-deprecated-september-2026/)
- Project history: a camera push-in made the crest outline melt; static-camera Grok Video 1.5 Lite shimmer clips kept the crest stable; gpt_image_2_5 xhigh reproduced the crest well from reference images — [brief, not independently sourced]

### Inferences
- For the crest the decisive variable is **camera and subject motion**, not model rank. The Vidlux finding (Kling Turbo most locked-off) and the owner's own Grok Lite result agree: models that move the product least preserve it best.
- A practical shortlist to A/B on one hero frame: Kling 3.0 / O3 Frames (start+end lock, cheap, strong human close-ups), MiniMax H3 (2K, top leaderboard, start+end), Grok 1.5 Lite (cheapest static shimmer), and Seedance 2.0 / 2.5 only when you need multi-reference identity or native audio. Veo 3.1 (32–80 credits per 8 s, start frame only at full tier) is poor value for this crest-locking need.
- Hands: no model is reliably good at a hand manipulating a small chain clasp. Plan shots where hands do simple, large motions (open a fist, lift a box lid, drape the chain), and cut away before fine finger work.

### Gaps
- No independent test of jewelry, rhinestones, small logos or lettering for any 2026 model.
- Runway (Gen-4.5 or later) and Vidu Q4 / HiDream were not evaluated: they are not on Higgsfield and no product-specific tests were found.
- Exact Artificial Analysis standings could not be checked at the source (fetch blocked).

## 3. Which workflows best prevent product (crest) morphing, and what is the recipe and credit cost per ad concept?

### Takeaway
The only near-guaranteed way to keep the licensed crest exact is to never let a video model redraw it in the final frames. Shoot or keep the real product (the real phone footage or a real packshot) and composite or track it over AI footage in post, or limit AI to a static camera with start = end frame locks and short clips. Generate hero stills first with gpt_image_2_5 xhigh from reference photos, then animate only around the product. Use motion transfer from a self-recorded phone video for human movement, and swap the person rather than the pendant.

### Cited Findings
- AI video morphing is the main reason clips fail commercially: the model predicts the next frames and causes "rapid pixel shifting (flickering) or structural warping (morphing)". The recommended fix is image-to-video from a high-resolution product photo, animating "the surrounding environment while keeping the product itself stable", from sharp, high-contrast, artifact-free source photos — [Dreamina/CapCut guide (vendor)](https://dreamina.capcut.com/ai-video/ai-video-motion-consistency-and-workflow); [Dreamina product-photo playbook](https://dreamina.capcut.com/ai-video/turn-product-photos-into-ai-videos)
- Higgsfield's own UGC pipeline keeps "real product labels and geometry" by passing the real product photo as a reference in every clip (`product_video_reference`). It writes ONE canonical product description reused "VERBATIM" in every prompt, including hand-relative size and "one honest imperfection". It warns that big readable logos/wordmarks "render as gibberish" — [HF-MCP ugc-video product-product-intake.md](https://higgsfield.ai)
- Hybrid compositing practice: AI shots are "tracked and composited in Adobe After Effects to seamlessly integrate with the live-action footage" (2026 FIFA World Cup opening project) — [Contra](https://contra.com/community/FXuHVRDg-hybrid-ai-live-action-opening). For logo animation, AI was used only for exploration and the final was "rebuilt, refined, and composited manually" — [Contra](https://contra.com/p/rbcrqFsR-ai-accelerated-logo-animation-and-motion-design)
- Integration checklist: match lighting, edges, color and motion (track camera motion from real footage and apply it to the AI element's position and scale). "It's easier to generate AI to match footage than to adjust footage to match AI" — [skillselion AI-VFX skill](https://skillselion.com/skills/omer-metin/skills-for-antigravity/ai-visual-effects). After Effects' motion tracker for logo areas — [Noble Desktop tutorial](https://blog.nobledesktop.com/learn/after-effects/cellphone-commercial-motion-tracking-to-remove-a-logo)
- Kling motion control: upload a reference video (poses, camera path, timing) plus a still. Don't re-describe the motion in the prompt, match the framing of the reference to the target shot (a full-body reference mapped onto a close-up "produces visible pose-squashing"), and keep prompts to about 500 characters and one beat — [Framia guide](https://framia.converge.ai/blog/kling-motion-control/); [AI Video Sensei](https://aivideosensei.com/prompts/kling-motion-control-prompts). Reference uploads are reported at up to 30 s, but one API page lists a 10 s max for image-oriented output — [Framia](https://framia.converge.ai/blog/kling-motion-control/); [muapi](https://muapi.ai/id/playground/kling-v3.0-pro-motion-control)
- Keep clips short ("under eight seconds") to avoid distortion and morphing — [Atlabs](https://www.atlabs.ai/blog/how-to-make-ai-videos-look-less-artificial-in-2026-(step-by-step-guide))
- Seedance 2.5 region-level edit ("point at the object… fix just that, and the rest of the clip stays untouched") — [Higgsfield blog via search](https://higgsfield.ai/blog/seedance-2-5-on-higgsfield-2026). Available as `seedance_2_5 mode=video_edit` (billed by source duration) — [HF-MCP](https://higgsfield.ai)
- Ad Multiplier edit mode replaces people or products in a 4–30 s source video "while preserving source motion, framing, cuts, timing… default audio" — [HF-MCP workflow catalog](https://higgsfield.ai)

### Inferences

**Crest-protection rules, in order of reliability**
1. **Real-plate rule:** for any shot where the crest is readable, use real footage or a real photo of the pendant. Film the phone-video yourself (crest real), or composite the real cut-out packshot (the store already has background-removed photos) onto AI footage and corner-pin/track it with CapCut keyframes, AE's tracker or ffmpeg `overlay`. Add a light grain and blur pass over the whole frame so it matches.
2. **Static-lock rule:** if AI must render the pendant, use a locked-off camera and `start_image` = `end_image` (or a near-identical end frame) on Kling 3.0 / O3 Frames, MiniMax H3 or Hailuo 2.3, with the motion limited to sparkle, light sweeps, hair or hoodie. A ping-pong or reversed loop of a good 3–5 s clip doubles the usable length for free.
3. **Hero-frame-first rule:** design every key frame as a still (gpt_image_2_5 xhigh 2K, 4.5 credits, with 2–3 real crest reference photos), fix any crest error in the still, then animate. Never let text-to-video invent the crest.
4. **Reveal via end frame:** for "3, 2, 1" or unboxing, use the closed fist or closed box as the start frame and the open hand with a sharp crest as the END frame. The model then has to arrive at a correct crest instead of drifting away from one. Cut on the reveal to a real packshot insert anyway.
5. **Swap the person, not the pendant:** with motion transfer (Kling 3.0 Motion Control, Genjutsu) or Ad Multiplier, drive the movement with your own phone video. Expect the generative pass to redraw the crest too, so plan to re-composite the real crest over the output.
6. **Cut-away editing:** keep the crest on screen in clean frames only. Mask transitions with whip-pans, hand occlusion or chain swing; never push in on the crest.

**Per-concept recipes and credit estimates (prices from the Q1 table; retries assume 3–4 attempts)**

| Concept | Recommended route | Est. credits |
|---|---|---|
| **Pendant sparkle / hero loop** | Real macro packshot or gpt_image_2_5 xhigh hero (4.5) → Grok 1.5 Lite 3 s static shimmer (3 each × 4 = 12) or Kling O3 Frames pro 5 s with start=end (6.25 × 3 ≈ 19) → ping-pong loop in post; optional MiniMax H3 2K test (10 × 2) | **15–45** |
| **Hoodie person, apartment, "3-2-1" reveal** | Best: film it yourself on a phone (real crest), optionally recast the person with Kling 3.0 Motion Control std 10 s (17 × 2–3 = 34–51), then re-composite the real crest. Full-AI alternative: 2 stills (fist closed / pendant shown, 9 credits) → Kling O3 Frames pro 5 s, static camera (6.25 × 4 = 25) → cut to real packshot. Countdown audio: real voice (free) or Polish TTS (~0.5) | **35–60** |
| **Chain put around the neck** | Hardest shot (hands + chain physics + crest). Record yourself doing it slowly, then Kling Motion Control pro 10 s (27 × 2 = 54), or a start frame (chain in hands) plus end frame (pendant resting on chest, crest sharp) on Kling 3.0 pro (8.75 × 4 = 35). Always end on a static close-up with a composited crest | **45–90** |
| **UGC talking head in Polish** | Cheapest reliable: AI person still (soul_2 ~1 or gpt_image_2_5 4.5) → silent Kling 3.0 pro 10 s talking clip (~17.5) → Polish voice (real recording, or ElevenLabs inside Higgsfield ~0.5–2) → Sync Lipsync 3 (54 per 15 s) ≈ 75. Premium: Seedance 2.5 omni_reference 720p 15 s with a Polish audio reference (105) or Marketing Studio V2 UGC 15 s (105); 1080p 15 s ≈ 240. Pendant shown only in B-roll inserts | **75–110 per 15 s** (240 at 1080p) |
| **Gift reaction** | Real reactions (friends/family) are free and more credible. AI version: start frame of a person opening the box → Kling 3.0 pro 5 s with sound (12.5 × 3) or Hailuo 2.3 for facial emotion (6 × 3); keep the pendant small or blurred in reaction shots and cut to a real close-up | **20–45** |
| **Unboxing** | Film it for real with the real box (0 credits). AI: Higgsfield's UGC unboxing pipeline (GPT Image 2 boards + Seedream cleanup + Seedance 2.5 1080p 15 s) ≈ 240+ credits per 15 s; at 720p ≈ 105. Cheaper: box-closed → box-open start/end frames on Kling (6.25–8.75 × 3) | **20–30 cheap / 105–250 premium** |
| **Polish captions / assembly / virality check** | CapCut (free) or Higgsfield video-montage; Virality Predictor on finals (cost unknown) | **0 + predictor (price unknown)** |

- Suggested split of the 937 credits: about 150 for a test phase (A/B Kling O3 Frames vs MiniMax H3 vs Grok Lite on the same hero frame; one Lipsync 3 Polish test), about 500 for production of 4–6 ads, and about 250 in reserve. Avoid Seedance 2.5 1080p except for one final hero spot.

### Gaps
- No tests found of Genjutsu `hf_mult_replace_object` or Ad Multiplier on tiny logos; whether they preserve or redraw a reference crest is unknown and needs one paid test.
- No published guide specific to CapCut tracking of jewelry over AI footage; the CapCut steps above are inference.
- Licensing: whether the FC Barcelona licence terms allow AI-rendered depictions of the crest was not researched. Check the licence or brand guidelines before publishing AI-rendered crests.

## 4. Which AI voice and lip-sync options produce natural Polish, and what do they cost?

### Takeaway
Polish TTS quality is a solved problem with ElevenLabs (available inside Higgsfield via `elevenlabs_v4` / `text2speech_v2`, or directly from $6/month with 10k characters free). Polish **lip-sync** is the weak link. Kling 3.0 native dialogue officially supports only EN/ZH/JA/KO/ES, Veo 3.1 is English-centric, and Seedance does not list Polish. The robust route is to record or generate the Polish audio first, then drive lips from it: Sync Lipsync 3 in Higgsfield (54 credits per 15 s), Seedance 2.x/2.5 with an `audio_references` input, or HeyGen Avatar IV. The most authentic option is a real Polish voice (the owner's own, possibly cloned with `create_voice`).

### Cited Findings
- Kling 3.0 natively supports lip-synced dialogue in five languages (English, Chinese, Japanese, Korean, Spanish); Polish is not listed — [Kling blog](https://kling.ai/blog/kling-video-3-omni-native-lip-sync-audio-guide); [Atlas Cloud comparison](https://www.atlascloud.ai/blog/ai-video-models-native-audio-compared)
- Veo 3.1's audio strength is "environmental and ambient sound rather than multilingual dialogue"; it handles English-centric speech and "lacks Kling 3.0's multilingual lip sync" — [Atlas Cloud](https://www.atlascloud.ai/blog/ai-video-models-native-audio-compared)
- Seedance 2.0: vendors claim "phoneme-level lip-sync across 8+ languages" (EN, Mandarin, JA, KO, Chinese dialects; Polish not named). A community skill file ranks Mandarin and English strongest and Japanese, Korean and Russian weaker. It recommends very short non-English lines or "a voice reference" so "the model syncs to your audio instead of synthesizing speech", which it calls "the most reliable field-reported path for non-English dialogue" — [cutout.pro](https://www.cutout.pro/learn/blog-seedance-2-0-audio-guide/); [tessl Seedance skill](https://tessl.io/registry/skills/github/Emily2040/seedance-2.0/seedance-audio). A Seedance 2.5 page claims 10+ languages without naming Polish — [seedance.tv](https://www.seedance.tv/blog/seedance-2-5-supported-languages)
- On Higgsfield, `seedance_2_0`, `seedance_2_5`, `minimax_h3`, `wan3_0`, `grok_video_v15` and `cinematic_studio_video_4_0` accept `audio_references`; `kling3_0` does not — [HF-MCP models_explore](https://higgsfield.ai)
- Higgsfield `dubbing` supports `pol` (45 credits per 15 s) and `sync_so` Lipsync 3 lip-syncs any video to any audio (54 credits per 15 s) — [HF-MCP](https://higgsfield.ai)
- ElevenLabs has a dedicated Polish TTS page with 10,000 free characters per month — [ElevenLabs Polish TTS](https://elevenlabs.io/ko/text-to-speech/polish). A Polish review says Multilingual v2 and v3 sound more natural than competitors in similar price ranges — [BIGVU (PL)](https://bigvu.tv/blog/pl/cennik-elevenlabs-2026-który-plan-5-456/). Plans (May 2026): Free $0 (10k credits), Starter $6, Creator $11 first month ($22 after), Pro $99. The API lists v3 at $100 per 1M chars and Flash/Turbo v2.5 at $50 per 1M — [Fora Soft](https://www.forasoft.com/learn/ai-for-video-engineering/articles-ai/elevenlabs-pricing-voice-cloning-no-fakes-act); [Gradium](https://gradium.ai/content/best-elevenlabs-alternatives-2026-tts-apis-voice-quality-price)
- ElevenLabs short clips (20–30 s) are "difficult to distinguish from a human voice actor", but long scripts drift with numerals and acronyms — [Provimedia](https://www.provimedia.de/en/blog/best-ai-voice-generators-2026)
- HeyGen: Avatar IV/V costs 20 credits per minute, lip-synced dubbing costs double, the Creator plan is $29/month (a 5-min Avatar IV video ≈ $4.83), Business is $149 + $20/seat, and it lists 175+ dubbing languages with lip-sync. Reviewers call Avatar IV "the clearest winner… for lip-sync and mouth tracking" — [Perso.ai review](https://perso.ai/blog/heygen-ai-dubbing-review-2026); [Creatify comparison (competitor)](https://creatify.ai/blog/heygen-vs-synthesia-(2026)-pricing-avatars-and-which-one-fits-your-team)
- Lip-sync roundups: no single best tool. Sync Labs is called the strongest pure lip-sync for existing video, and Rask AI lags on fast speech — [VideoDubber (vendor)](https://videodubber.ai/blogs/best-lip-sync-tools-2026/); [ecommercefastlane](https://ecommercefastlane.com/best-ai-lip-sync-video-dubbing-tools-2026/)
- "Lips that almost match the audio break realism faster than most visual flaws" — [Atlabs](https://www.atlabs.ai/blog/how-to-make-ai-videos-look-less-artificial-in-2026-(step-by-step-guide))
- `seed_audio` priced one Polish sentence at 0.5 credits (Polish output quality untested) — [HF-MCP get_cost](https://higgsfield.ai)

### Inferences
- Recommended Polish stack inside Higgsfield: write a short line (5–10 words per beat) → generate with ElevenLabs v4 (via `elevenlabs_v4` or `text2speech_v2 variant=elevenlabs`; pick a voice by previewing, since Higgsfield voices carry no language tags) or record a real person → lip-sync with Lipsync 3 (`sync_so`), or pass it as `audio_references` to Seedance 2.0/2.5 → burn Polish captions in post.
- Polish is phonetically dense (consonant clusters such as "szcz" and "prz"), so Kling's native audio will likely mispronounce it or speak with an accent; do not rely on it for Polish dialogue. This is inference: no Polish test was found.
- If spending outside Higgsfield, HeyGen Creator ($29/month) is the best-reviewed lip-sync for talking heads. ElevenLabs Starter ($6) is enough for ad-length scripts. Arcads and Captions AI actors were not covered by any source found.
- For the "3, 2, 1" concept no lip-sync is needed: off-screen voice or on-screen text plus trending audio avoids the hardest problem entirely.

### Gaps
- No hands-on Polish lip-sync test was found for Sync Lipsync 3, Seedance, HeyGen or ElevenLabs dubbing.
- Pricing and Polish support for Arcads, Captions (Mirage) and ElevenLabs' own lip-sync or dubbing product were not found.
- Whether Higgsfield `dubbing` preserves lip-sync, and whether `elevenlabs_v4` preset voices include native Polish speakers.

## 5. What makes AI ads look authentic versus "AI slop" in 2026, and what raises realism? (Plus the disclosure rules that now apply)

### Takeaway
Low-production, phone-shot, creator-style content still beats polished renders, and consumer trust in obviously-AI ads is eroding. Realism comes from prompting camera behavior and imperfection (handheld, window light, grain, restrained expressions), short clips, perfect lip-sync, real audio, and mixing real footage with AI. Since August 2026, realistic AI people or scenes in EU ads, and in TikTok ads, must be labelled as AI. Fabricated "customer testimonial" UGC is risky both legally and ethically.

### Cited Findings
- Over 30% of US adults say AI in ads makes them less likely to choose a brand (CivicScience via eMarketer). 78% of marketers call UGC important versus 28% for AI-generated content. eMarketer's advice is that "human-generated content drives credibility" — [eMarketer FAQ](https://www.emarketer.com/insights/social-media-forecasts-worldwide); [eMarketer on AI slop](https://www.emarketer.com/content/youtube-ai-slop-surge-risks-brand-safety-viewer-trust)
- Deliberately low-production content, shot on phones with natural light, continues to outperform polished studio content — [Balistro (May/Jun 2026)](https://www.balistro.com/blog/ad-creative-trends-dominating-social-media-2026). Organic-creator-style ads reportedly beat polished brand videos by about 22% on view-through rate (attributed to TikTok Creative Center, unverified) — [Chatcut](https://chatcut.io/blog/create-ads-for-tiktok-video-with-ai). The vendor claim that "if your synthetic video feels synthetic, you get ignored" is accompanied by unsourced CTR uplift numbers — [NovaPixel](https://novapixeldev.com/blog/ai-ugc-ads-authenticity-playbook-2026)
- Realism prompting: describe camera hardware and behavior (lens, light, movement, "handheld framing", "light film grain") rather than "cinematic, ultra realistic, 4K", and drop "flawless", "perfect" and "8K hyperrealistic". A UGC iPhone template calls for smartphone depth of field, an extended-arm selfie angle, a thumb partly in frame, window light and mild grain — [ClipSpeed](https://www.clipspeed.ai/blog/ai-video-prompt-guide.html); [videoai.me iPhone look](https://videoai.me/blog/how-to-make-ai-videos-that-look-filmed-on-iphone); [Pixelbin](https://www.pixelbin.io/blog/how-to-make-realistic-ai-videos)
- AI tells: over-smoothed or waxy skin, over-sharpened edges, exaggerated expressions. Finishing pass: light grain, slight blur, a desaturated grade, and upscaling so compression softness doesn't read as AI blur — [Atlabs](https://www.atlabs.ai/blog/how-to-make-ai-videos-look-less-artificial-in-2026-(step-by-step-guide)); [shedoesai](https://shedoesai.beehiiv.com/p/low-quality-ai-is-losing)
- Higgsfield's own UGC character and monologue guidance: an "anti-AI / unretouched" realism engine for character sheets; in monologues, remove "AI-tell warm-ups, generic praise, repetition"; never bake text into generation (add text in post) — [HF-MCP character-sheet + ugc-video unboxing.md](https://higgsfield.ai)
- **EU AI Act Art. 50** transparency duties apply from 2 Aug 2026. Draft Commission guidance (8 May 2026) defines a deepfake as AI-generated or manipulated image, audio or video that "resembles real people or events and could be mistakenly perceived… as genuine", with no intent required. A law firm notes this can cover realistic AI product images used in advertising. Fines run up to €15M or 3% of turnover. A voluntary Code of Practice on marking was published 10 Jun 2026 — [SRD Rechtsanwälte](https://www.srd-rechtsanwaelte.de/en/blog/deepfake-labelling-under-the-ai-act-what-the-new-eu-guidance-clarifies); [Lausen](https://lausen.com/en/section-504-of-the-ai-act-what-organisations-must-label-as-ai-content-from-august-2026/); [artificialintelligenceact.eu](https://artificialintelligenceact.eu/?p=6131)
- **TikTok:** the AIGC label is a disclosure requirement, not a ban. Ads with realistic AI-generated scenes or people reportedly require AI disclosure since a 21 Jul 2026 ads-policy update. Slideshows of real product photos generally fall outside the label. Enforcement is reported as uneven — [Cinerads](https://www.cinerads.com/blog/tiktok-ai-content-policy); [Stellar Search](https://www.stellarsearch.co.uk/insight/tiktoks-ai-ad-disclosure-rules-are-live-what-brands-running-ai-creative-need-to-do-now); [ainauten](https://news.ainauten.com/en/story/tiktoks-policy-for-ai-ads-isnt-working)

### Inferences
- The strongest authenticity strategy for Vellano is **hybrid**: a real hand, real pendant, real box and real Polish voice, with AI used for setting, extra B-roll, person variants and sparkle. This also shrinks the deepfake-label surface: real footage needs no label, and an AI-generated person does.
- Concrete tricks: vertical phone framing; slight handheld drift added in post rather than generated camera moves (protects the crest); window or lamp light in an ordinary Polish flat; a hoodie with a little lint; imperfect nails; ambient room tone; captions in CapCut style; 6–12 s total for hooks; avoid perfect symmetry and glossy skin.
- Don't present an AI actor as a real customer giving a testimonial. Higgsfield's own workflow refuses fabricated reviews, and EU and TikTok rules require AI labels on realistic synthetic people. Frame AI-person ads as "styl prezentacji" rather than reviews, and add "Wideo wygenerowane z użyciem AI" or TikTok's AIGC toggle.

### Gaps
- No rigorous, independent study of AI-UGC versus real-UGC conversion on TikTok or Meta in 2026; all uplift figures found are vendor claims.
- Polish-specific rules (UOKiK guidance on influencer and AI advertising, fake reviews) were not researched.
- Whether TikTok's AIGC ad label measurably reduces reach (claims exist, no data found).

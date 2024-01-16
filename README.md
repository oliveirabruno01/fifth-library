:information_source: **Attribution:** This work includes material taken from the System Reference Document 5.1 (“SRD 5.1”) by Wizards of
the Coast LLC and available at https://dnd.wizards.com/resources/systems-reference-document. The
SRD 5.1 is licensed under the Creative Commons Attribution 4.0 International License available at
https://creativecommons.org/licenses/by/4.0/legalcode.



# fifth-library
This repo is aimed to be where I dump some tests I've been making on the junction of two passions: interacting with LLMs and creating 5E campaings/worlds;

Currently this contains:
- **Original monsters**, creatures and NPCs sheets using a single format, as JSON at [monster_sheets/original.json](monster_sheets/original.json). This was normalized using [Tabyltop](https://github.com/Tabyltop/CC-SRD) and [u/droiddruid](https://www.reddit.com/r/dndnext/comments/43a09o/srd_monsters_in_json_format/) contributtions + some missing fields that I scraped from original SRD doc.
- **Lore-augmented monsters**: the above sheets but slightly augmented by ``openchat/openchat-7b`` to include "description" and "additionals" fields. Additionals is a list of character's lore pieces. At [monster_sheets/augmented-lore.json](monster_sheets/augmented-lore.json). The lore creation process used in-context learning from GPT-4 generations, to generate a random number of CoT samples (from @1 to @5). Samples were ranked and selected by a "Judge", also acted by ``openchat/openchat-7b`` with in-context learning from larger models (and me).


# Directions
In the future I may or not:
- Add all SRD spells, also facilitated by u/droidruid esforces
- Add a dataset with completely random custom monsters, using LLMs
- Upload the code I used to parse everything together and to generate the augmented lores
- Finish and upload an explorer.

H/T to [OpenRouter](https://openrouter.ai/models/openchat/openchat-7b) for providing 0-cost inference

# Funfact
While cooking this, before I found u/droiddruid compilation, I noticed an apparently strange behavior either on GPT-4 and lesser powerful models such as GPT-3.5 and domestic llamas (tried with 7b and 34b): 

these models are kinda addicted to writing a ``legendary_actions`` field, even when explicitly told not. At the time I was using something like ``is_legendary: boolen`` inside an "action" object but 90% of times it wouldn't get it right. 

It turned out that ``legendary_actions`` is the format used by u/droiddruid, and it's aguarbly the best json formatted compilation of SRD. Can we infer that GPTs are trained - a lot - on that? u/droiddruid told us that the format is "compatible with a few different resources, including my own Fifth Edition DM Tools.", so we also can guess that this format is used elsewhere on the wild.

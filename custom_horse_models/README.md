This is the README associated for custom horse models. 
All thoughts, notes, etc are associated in this file and will correlate to other files within this folder. 

Example Folder Layout: 

[customs] > [stream], fxmanifest.lua, metapeds.ymt > all ymt and texture files inside of [stream]

When you're wanting to make a custom horse model within the world of RedM, you're going to want to read up on Expression values within the world of RDR2 and their ped models. 
Highly recommend this link here, credits to T3CHMAN whom made this, along with another very in-depth github repo about RedM/RDR2 modding research. 
https://pastebin.com/Ld76cAn7

In this file are horse expressions, and human ped expressions. Some are fully translated, some are yet to be translated. 
These values are going to be used in natives such as SetCharExpression(ped, index, value) (Reference here: https://rdr3natives.com/?native=0x5653AB26C82938CF)

This is part of the process when you're wanting to manipulate the expressions in a script. You'll use this native, along others, to create a new ped model (overriding an existing one ONLY in that script - not other scripts) and then script the new expressions into your designated horse, stable script, etc. 

These values usually range from -2.0 to 2.0. 

You can also make custom models a much easier way, and this is just streaming a new .ymt file in your server's resources. 
See example file: A_C_Horse_Winter02_01.ymt (Oakfen Hanoverian Model)

In this file, you can find an entirely translated ymt file, since when you find these in Codex they are entirely encrypted. Or, some ymt's have "UNK_MEMBER" as value names. This file will give you everything from tints, albedos, coat shine, scale, etc. 

All of the "p_c_horse_01_head_000" that you see is going to be the head textures of the horse, and the p_c_horse_01_hand_000" is going to be the body texture of the horse. In this <Item> block, you can define the albedo textures, normal, and material. Along with tints. 

You can find these in Codex just by looking up "p_c_horse_01_head_000_c0_" and this will give all. 
Some are found under "p_c_horse_merge", and "mp_horse_01" 

You can make your custom horse with the same expression values found in this file, and editing them directly. 
You can stream the file directly into your server - and it will replace that specific horse model for everyone's horse model in the game. 
To stream it correctly, you need the correct data file mounter. You can see all of them here: https://github.com/draobrehtom/redm-data-file-mounters/blob/main/README.md
The one you need for ymt's is: METAPED_ASSETS

Make an fxmanifest.lua, plop the file mounter in there, and then stream your ymt in the same folder. Restart server - and you're done. 
This will alter the expressions from the model you picked, so it will increase the associated expression for that horse. 

You will also need the metapeds.ymt file, where you need to create your own and stream it. 
You can find this file in Codex, and you need to export in Codex for it to be recognized when you stream it. 
The only thing you ned to put in this file is the name of the model you are replacing. 

That's mainly it for wanting to make your own custom horse models - I will not teach you how to script it. Teach yourself. I gave the resources you need to do it.

Here is a breakdown of things that could be involved in your very own horse script, or stable script: 

- Where expressions are placed: inline in templates, in config files, or in script source (identify exact file(s) that contain them).
- Lexing/parsing: tokenization of expression strings and creation of an AST or token stream.
- Binding: lookup of identifiers against the script runtime/context (global vars, local scope, injected services).
- Type/validation: optional static checks or runtime validation of operand types and allowed operations.
- Compilation/evaluation: either interpreted evaluation of the AST or compilation to a function/closure that the script calls.
- Integration API: exposing an evaluate/execute function on the runtime that scripts call with a context object (variables, functions, permissions).
- Error handling: capture parse and runtime errors, map back to source positions, and surface/log meaningful messages.
- Security/sandboxing: restrict allowed functions/operators, sanitize inputs, and enforce time/memory limits if needed.
- Caching/optimizations: cache parsed ASTs or compiled functions to avoid repeated parsing.
- Testing/coverage: unit tests for parsing, evaluation, edge cases, and security rules.

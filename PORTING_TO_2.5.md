# Porting 1.8.2 AIs -> Fortnite 2.5

Done in this copy:
- [x] Version lock in `dllmain.cpp` changed from 1.82 to 2.5
- [x] Window titles changed
- [x] .gitignore added (no build output / DLLs / game files)

TODO (needs a Fortnite 2.5 build you own):
1. **Regenerate SDK offsets.** Dump a 2.5 server build with Dumper-7 and update
   `Source Code/SDK/Offsets.h`, `Offsets_1_8_2.inc`, `OffsetsInfo_1.8.2.json`
   (GObjects, AppendString, GNames, GWorld, ProcessEvent + index).
2. **Build** in Visual Studio 2022 (x64, Release). Fix compile errors, if any.
3. **Test the base server first** with bots off (`cheat pause bot spawn`):
   - Does it start and print "FN 2.5"?
   - Can a client join and get into the match?
   - Look at which `Finders.cpp` patterns fail (console shows what wasn't found).
4. **Re-record map locations.** `BakedPlaces.h` is 1.8.2 map data. Use the place
   dump hotkey (F5) in 2.5 and replace it.
5. **Check BotAI.cpp** for class/actor names that differ in 2.5.
6. **Client DLL** (`Four_E_Zero_H Client`): update its patterns/hooks for 2.5 too.

Rules: don't commit game files, don't sell/monetize, keep the GPLv3 license and
credits to 4e0h, apathy, ploosh, pongo, ralzify.

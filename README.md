# Type-in Font Search for EffectCraft

Search directly in the font selection field in Character and Properties. The font name and search share one row, with case-insensitive results below. Select with the mouse or arrow keys and Enter; Escape closes the list. Supports Undo and applying a font to selected text.

## Apply the patch

This patch targets [EffectCraft](https://github.com/storytold/effectcraft) commit `608d1b077b65bb7591f26be587a2a5a47f4278bc`.
It can be applied independently of the other two feature patches. For all three features together,
full source and a Windows build, see [effectcraft-custom](https://github.com/kikikikier/effectcraft-custom).

```powershell
git clone https://github.com/kikikikier/effectcraft-type-in-font-search.git
git clone https://github.com/storytold/effectcraft.git
Set-Location effectcraft
git checkout 608d1b077b65bb7591f26be587a2a5a47f4278bc
git apply --check ../effectcraft-type-in-font-search/effectcraft-type-in-font-search.patch
git apply ../effectcraft-type-in-font-search/effectcraft-type-in-font-search.patch
# Apply the shared custom-build branding patch once, even when combining features.
git apply ../effectcraft-type-in-font-search/custom-build-branding.patch
cargo +1.95.0 build --locked --release -p effectcraft
```

Compatibility with newer upstream versions must be checked before applying the patch.
When distributing a modified build, also remove the trademark assets in `docs/brand/`
and their images in the documentation, as required by the upstream terms.

## Validation

```powershell
cargo +1.95.0 test --release -p effectcraft-ui-egui --test ui_font_search --test ui_text_edit
```

Each patch was checked against the clean base commit. All six application orders of the three
patches produce the same source tree. Combined-build results and known limitations are documented
in the [build report](https://github.com/kikikikier/effectcraft-custom/blob/main/CUSTOM-BUILD.md).

## Related repositories

- [Infinite Drag](https://github.com/kikikikier/effectcraft-infinite-drag)
- [TextBox Plugin](https://github.com/kikikikier/effectcraft-textbox-plugin)
- [All three features together](https://github.com/kikikikier/effectcraft-custom)

## Credits and license

Based on EffectCraft by the ArtCraft Team and contributors. This is an independent community
addition, not an official upstream release. Code is licensed under **MIT OR Apache-2.0**;
upstream notices are preserved in [NOTICE](NOTICE), [LICENSE-MIT](LICENSE-MIT)
and [LICENSE-APACHE](LICENSE-APACHE).

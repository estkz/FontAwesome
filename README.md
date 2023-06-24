# FontAwesome
The FontAwesome icons can be loaded from memory using minimal source code, utilizing a static const unsigned int array containing bytes, which can be employed in frameworks like imgui.

```cpp

// Add the following code inside your Initialize or (ImGui Creation) function.
// Declare ImGui::GetIO();
ImGuiIO& io = ::ImGui::GetIO();

// Declare icon_ranges | Icons In Menu.
static const ImWchar icon_ranges[]{ 0xf000, 0xf3ff, 0 };
ImFontConfig icons_config;

// Avoid conflict with other fonts.
icons_config.MergeMode = true;

// Make Icons Cleaner
icons_config.PixelSnapH = true;
icons_config.OversampleH = 3;
icons_config.OversampleV = 3;

// Function call, which adds the FontAwesome icons and making it available for rendering in ImGui.
icons_font = io.Fonts->AddFontFromMemoryCompressedTTF(font_awesome_data, font_awesome_size, 19.5f, &icons_config, icon_ranges);

// Define this outside your Initialize (ImGui Creation) function.
inline ImFont* icons_font = nullptr;

// Example Code | Place this in your render function.
ImGui::PushFont(icons_font);
ImGui::Text(ICON_FA_AXE); // You can find all the defined icons in font_awesome.h
ImGui::PopFont();
```

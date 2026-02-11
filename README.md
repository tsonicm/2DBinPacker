# 2D Bin Packing Visualizer

A professional, interactive web application for visualizing and optimizing 2D bin packing solutions with client-based segregation and collision prevention.

![License](https://img.shields.io/badge/license-GPL%203.0-blue.svg)
![AI-Assisted](https://img.shields.io/badge/AI-Assisted-purple.svg)

## ⚠️ Development Notice

This application was created with the assistance of AI tools (GitHub Copilot / Claude), which helped in generating code, implementing features, and solving technical challenges throughout the development process.

## 🎯 Overview

The 2D Bin Packing Visualizer is a single-file HTML application that helps you efficiently pack rectangular packages into a 2D bin space. It's designed for logistics, warehouse management, and shipping optimization scenarios where you need to visualize how packages fit together with strict client segregation.

## ✨ Key Features

### Core Functionality
- **Maximal Rectangles Algorithm** - Best Short Side Fit heuristic with constraint-based sorting for optimal space utilization
- **Strict Client Segregation** - Sequential client processing ensures packages stay grouped without interleaving
- **Smart Space Management** - Detects and penalizes unusable narrow spaces (<30cm), prioritizes large constraining packages first
- **Interactive Visualization** - Full canvas with zoom (50%-500%), pan, and drag capabilities
- **Unpacked Package Display** - Visual representation of unpacked packages below the bin with wrapping layout
- **Alt+Click Placement** - Manually place unpacked packages into the bin with automatic position finding
- **Remaining Space Visualization** - Toggle display of remaining horizontal space for each rightmost package
- **Multi-Selection & Group Dragging** - Select multiple packages with Ctrl/Cmd+Click and move them together
- **Smart Collision Prevention** - Hold Shift while dragging (single or groups) to prevent package overlap
- **Package Rotation** - Double-click or press 'R' to rotate packages 90°

### Package Management
- **Reference Number System** - Extracts last 6 digits from EAN13 barcodes (auto-trims leading zeros)
- **Bulk Import** - Tab-separated format: `refNo [tab] LxW [tab] comment [tab] client`
- **Editable Packages** - Modify packages after adding them
- **Smart Padding System** - Adds 3cm padding for sizes 77 and 117, 5cm for all other standard sizes (50, 60, 70, 90, 100, 110)
- **Client Assignment** - Organize packages by client with 10-color palette

### Visual Guides
- **80cm Height Markers** - Blue dotted lines every 80cm (vertical axis)
- **2m Width Markers** - Red dotted lines every 2m with meter labels (horizontal axis)
- **Start/End Axis Markers** - 0m marker at bin start and total length marker at bin end (top of bin)
- **Dynamic Scaling** - Text and elements scale intelligently with zoom level
- **Color-Coded Display** - Each client gets a unique color for easy identification

### Export & Statistics
- **PDF Export** - A4 landscape format with color-coded layout, axis markers, and complete package list
- **Real-Time Statistics** - Bin area, package area, utilization percentage, packed count
- **Smart Unit Display** - Automatically converts to m² for large areas (≥10,000 cm²)

## 🚀 Usage

### Getting Started
1. Open `2D Bin Packing Visualizer.html` in any modern web browser
2. Set your bin dimensions (width × height in cm)
3. Add packages using one of three methods:
   - **Manual Entry**: Fill in reference number, dimensions, comment, and client
   - **Bulk Import**: Paste tab-separated data in the format shown
   - **Edit Existing**: Modify packages after adding them
4. Click "Visualize Packing" to see the optimized layout

### Bulk Import Format
```
123456	240x120	Fragile	Client A
234567	240x120	Heavy	Client B
345678	150x100	Standard	Client A
```
Format: `refNo [tab] lengthxwidth [tab] comment [tab] client`

### Interactive Controls
- **Alt/Option + Click** - Place unpacked packages (shown below bin) into the bin automatically
- **Drag packages** - Click and drag to reposition
- **Ctrl/Cmd + Click** - Multi-select packages (gold highlight shows selection)
- **Group Drag** - Drag any selected package to move entire group together
- **Shift + Drag** - Prevents overlap, slides along obstacles (works with single or groups)
- **Escape** - Clear selection
- **Double-click** - Rotate package 90°
- **Press 'R'** - Rotate hovered package
- **Scroll** - Zoom in/out (50%-500%)
- **Drag empty space** - Pan around the canvas
- **Reset button** - Return to 100% zoom and center view
- **Show Remaining Space** - Toggle display of remaining horizontal space measurements

### Example Test Suite (1360×245 bin)
```
123456	235x115	Fragile - Large	Client A
234567	235x115	Heavy - Large	Client B
345678	235x115	Standard	Client A
456789	235x115	Express	Client B
567890	145x95	Medium Box	Client A
678901	145x95	Medium Heavy	Client B
789012	145x95	Standard Med	Client A
890123	145x95	Priority	Client B
901234	115x75	Small Pallet	Client A
012345	115x75	Quick Ship	Client B
111111	115x75	Compact	Client A
222222	115x75	Rush Order	Client B
333333	75x55	Small Box A	Client A
444444	75x55	Small Box B	Client B
555555	75x55	Delicate	Client A
666666	75x55	Standard S	Client B
777777	55x35	Mini Pack	Client A
888888	55x35	Tiny Box	Client B
999999	235x35	Long Thin	Client A
100000	145x55	Flat Pack	Client B
```

## 🛠️ Technical Details

### Technology Stack
- **Pure HTML/CSS/JavaScript** - No dependencies beyond jsPDF
- **jsPDF v2.5.1** - For PDF generation
- **Canvas API** - For visualization rendering

### Algorithm
- **Maximal Rectangles Method** with Best Short Side Fit heuristic
- **Sequential Client Processing** - Each client's packages are packed completely before moving to the next client
- **Constraint-Based Sorting** - Large packages near bin dimensions are placed first to minimize unusable space
- **Strict Adjacency Enforcement** - Packages must touch same-client packages (5M+ score bonus for touching)
- **Unusable Space Detection** - Heavily penalizes orientations creating gaps <30cm (-50k to -100k penalties)
- **Free Rectangle Management** - Maximal rectangles split into 4 sub-rectangles, with pruning and merging
- **Automatic Rotation** - Tests both orientations, rejecting those that create narrow slivers

### Browser Compatibility
- Chrome/Edge (recommended)
- Firefox
- Safari
- Any modern browser with Canvas and ES6 support

## 📊 Features Breakdown

| Feature | Description |
|---------|-------------|
| **Algorithm** | Maximal Rectangles with Best Short Side Fit, constraint-based sorting |
| **Client Segregation** | Sequential processing, no interleaving, strict adjacency enforcement (5M+ bonus) |
| **Space Optimization** | Detects unusable gaps (<30cm), penalizes narrow slivers, merges adjacent free rects |
| **Dimensions** | Integer display with smart padding (3cm for 77/117, 5cm for others) |
| **Reference Numbers** | Last 6 digits of EAN13, leading zeros removed |
| **Client Grouping** | 10 distinct colors, packages must touch same-client packages |
| **Unpacked Display** | Visual packages below bin, wrapping horizontally, Alt+Click to place |
| **Remaining Space** | Green measurement lines showing horizontal space from rightmost packages |
| **Multi-Selection** | Ctrl/Cmd+Click to select multiple packages, gold highlight |
| **Group Operations** | Move multiple packages together, maintaining formation |
| **Collision Detection** | Shift-drag with sliding (works with single packages or groups) |
| **Guide Lines** | 80cm (height) and 2m (width) visual markers |
| **Axis Markers** | 0m start and total length end markers at top |
| **Statistics** | Auto-converts to m² for areas ≥1 m² |
| **PDF Export** | Professional A4 landscape format with axis markers |

## 🎨 Color Palette

The application uses a 10-color palette for client identification:
- Blue (#3b82f6), Green (#10b981), Orange (#f59e0b), Red (#ef4444)
- Purple (#8b5cf6), Pink (#ec4899), Cyan (#06b6d4), Lime (#84cc16)
- Deep Orange (#f97316), Indigo (#6366f1)

## 📝 Use Cases

- **Logistics Planning** - Optimize truck/container loading with improved space efficiency
- **Warehouse Management** - Plan storage layouts with strict client segregation
- **Shipping Optimization** - Minimize shipping costs by maximizing space utilization
- **Multi-Client Operations** - Keep different clients' packages completely separated and accessible
- **Pallet Configuration** - Design efficient pallet arrangements avoiding narrow unusable gaps
- **Complex Constraints** - Handle packages with dimensions near bin limits efficiently
- **Manual Reorganization** - Select and reposition multiple packages to optimize manually
- **Space Analysis** - Visualize remaining space and identify packing inefficiencies

## 🔄 Version History

### Version 1.3 (Current)
- **Maximal Rectangles Algorithm** - Replaced Guillotine with more efficient Maximal Rectangles algorithm
- **Best Short Side Fit** - Superior heuristic for minimizing wasted space
- **Constraint-Based Sorting** - Packages near bin dimensions sorted first to handle most constraining items early
- **Strict Client Segregation** - Sequential processing ensures no client interleaving, packages stay grouped
- **Adjacency Enforcement** - 5M+ score bonus for touching same-client packages, ensuring tight clustering
- **Unusable Space Detection** - Detects and heavily penalizes (<30cm gaps) orientations creating narrow slivers
- **Smart Rectangle Splitting** - Maximal rectangles subdivided into 4 sub-rectangles (left, right, top, bottom)
- **Rectangle Pruning & Merging** - Removes redundant free rectangles and merges adjacent spaces
- **Enhanced Space Efficiency** - Significantly better packing density while maintaining client grouping

### Version 1.2
- **Unpacked Package Visualization** - Packages that don't fit are displayed below the bin with wrapping layout
- **Alt+Click Placement** - Manually place unpacked packages into the bin with automatic position finding
- **Smart Position Finding** - Automatically finds the best available position (corners first, then grid search, tries rotation)
- **Remaining Space Measurements** - Toggle visualization showing horizontal space from each rightmost package to bin edge
- **Dynamic Space Display** - Green measurement lines with distance labels (in cm) update as packages are moved
- **Multi-Row Detection** - Intelligently identifies rightmost package in each row for accurate measurements
- **Enhanced Legend** - Reorganized controls with clear sections for placing, moving, multi-selection, rotation, and view controls
- **Horizontal Axis Markers** - 0m and final bin length markers at top of bin (both visualizer and PDF)
- **Landscape PDF Export** - Changed from portrait to landscape orientation for better bin visualization
- **Improved Print Layout** - Axis markers help with physical measurements during loading

### Version 1.1
- **Multi-Selection** - Ctrl/Cmd+Click to select multiple packages
- **Group Dragging** - Move multiple packages together while maintaining their relative positions
- **Enhanced Collision Prevention** - Shift-drag now works with groups, treating them as a single entity
- **Visual Selection Indicators** - Gold glowing border highlights selected packages
- **Keyboard Shortcuts** - Escape to clear selection, improved Ctrl/Cmd support
- Selection state management - Auto-clears on repack or when clicking empty space

### Version 1.0
- Client-based package grouping and segregation
- Smart collision prevention with sliding and snapping
- Dynamic font scaling for high zoom levels
- Automatic unit conversion (cm² ↔ m²)
- Enhanced guide lines (80cm height, 2m width markers)
- Integer dimension display throughout
- Smart padding system: 3cm for sizes 77 and 117, 5cm for all other standard sizes
- Interactive drag, rotate, zoom, and pan controls
- PDF export functionality (A4 format)
- Bulk import via tab-separated format
- Reference number system (EAN13 last 6 digits)

## 📄 License

GPL 3.0 License - This application is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

## 🤖 AI Acknowledgment

This project was developed with significant assistance from AI tools (GitHub Copilot / Claude Sonnet 4.5). AI was used for:
- Code generation and implementation
- Algorithm optimization
- Feature design and refinement
- Bug fixing and debugging
- UI/UX improvements
- Documentation

## ℹ️ Project Status

This application is actively maintained and improved. Recent updates include a complete algorithm overhaul to Maximal Rectangles for superior space efficiency while maintaining strict client segregation.

---

**Note**: All dimensions are in centimeters unless otherwise specified. The application automatically adds padding to entered dimensions for safety margins: 3cm for standard sizes 77 and 117, 5cm for all other sizes (50, 60, 70, 90, 100, 110). The Maximal Rectangles algorithm with constraint-based sorting ensures optimal packing while keeping client packages grouped together without interleaving.
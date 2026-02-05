# 2D Bin Packing Visualizer

A professional, interactive web application for visualizing and optimizing 2D bin packing solutions with client-based segregation and collision prevention.

![License](https://img.shields.io/badge/license-GPL%203.0-blue.svg)
![AI-Assisted](https://img.shields.io/badge/AI-Assisted-purple.svg)

## ⚠️ Development Notice

This application was created with the assistance of AI tools (GitHub Copilot / Claude), which helped in generating code, implementing features, and solving technical challenges throughout the development process.

## 🎯 Overview

The 2D Bin Packing Visualizer is a single-file HTML application that helps you efficiently pack rectangular packages into a 2D bin space. It's designed for logistics, warehouse management, and shipping optimization scenarios where you need to visualize how packages fit together.

## ✨ Key Features

### Core Functionality
- **Guillotine Bin Packing Algorithm** - Best Area Fit heuristic for optimal space utilization
- **Client-Based Segregation** - Automatically groups and color-codes packages by client
- **Interactive Visualization** - Full canvas with zoom (50%-500%), pan, and drag capabilities
- **Smart Collision Prevention** - Hold Shift while dragging to prevent package overlap
- **Package Rotation** - Double-click or press 'R' to rotate packages 90°

### Package Management
- **Reference Number System** - Extracts last 6 digits from EAN13 barcodes (auto-trims leading zeros)
- **Bulk Import** - Tab-separated format: `refNo [tab] LxW [tab] comment [tab] client`
- **Editable Packages** - Modify packages after adding them
- **Automatic Padding** - Adds 5cm safety margin to all dimensions
- **Client Assignment** - Organize packages by client with 10-color palette

### Visual Guides
- **80cm Height Markers** - Blue dotted lines every 80cm (vertical axis)
- **2m Width Markers** - Red dotted lines every 2m with meter labels (horizontal axis)
- **Dynamic Scaling** - Text and elements scale intelligently with zoom level
- **Color-Coded Display** - Each client gets a unique color for easy identification

### Export & Statistics
- **PDF Export** - A4 format with color-coded layout and complete package list
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
- **Drag packages** - Click and drag to reposition
- **Shift + Drag** - Prevents overlap, slides along obstacles, snaps to nearest empty space
- **Double-click** - Rotate package 90°
- **Press 'R'** - Rotate hovered package
- **Scroll** - Zoom in/out (50%-500%)
- **Drag empty space** - Pan around the canvas
- **Reset button** - Return to 100% zoom and center view

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
- **Guillotine Method** with Best Area Fit
- **Client-First Grouping** - Packs packages by client to prevent mixing
- **Free Rectangle Management** - Efficient space tracking and splitting
- **Automatic Rotation** - Tests both orientations for best fit

### Browser Compatibility
- Chrome/Edge (recommended)
- Firefox
- Safari
- Any modern browser with Canvas and ES6 support

## 📊 Features Breakdown

| Feature | Description |
|---------|-------------|
| **Dimensions** | Integer display with automatic 5cm padding |
| **Reference Numbers** | Last 6 digits of EAN13, leading zeros removed |
| **Client Grouping** | 10 distinct colors, segregated packing |
| **Collision Detection** | Shift-drag with sliding and snap-to-empty |
| **Guide Lines** | 80cm (height) and 2m (width) visual markers |
| **Statistics** | Auto-converts to m² for areas ≥1 m² |
| **PDF Export** | Professional A4 format with color coding |

## 🎨 Color Palette

The application uses a 10-color palette for client identification:
- Blue (#3b82f6), Green (#10b981), Orange (#f59e0b), Red (#ef4444)
- Purple (#8b5cf6), Pink (#ec4899), Cyan (#06b6d4), Lime (#84cc16)
- Deep Orange (#f97316), Indigo (#6366f1)

## 📝 Use Cases

- **Logistics Planning** - Optimize truck/container loading
- **Warehouse Management** - Plan storage layouts
- **Shipping Optimization** - Minimize shipping costs by maximizing space
- **Pallet Configuration** - Design efficient pallet arrangements
- **Multi-Client Operations** - Keep different clients' packages separated

## 🔄 Version History

### Current Version (v3)
- Client-based package grouping and segregation
- Smart collision prevention with sliding and snapping
- Dynamic font scaling for high zoom levels
- Automatic unit conversion (cm² ↔ m²)
- Enhanced guide lines (80cm height, 2m width markers)
- Integer dimension display throughout
- 5cm automatic padding on all dimensions

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

## 🙏 Contributing

While this is a single-file application primarily developed with AI assistance, contributions, suggestions, and bug reports are welcome!

## 📧 Contact

For questions, issues, or feature requests, please open an issue in the repository.

---

**Note**: All dimensions are in centimeters unless otherwise specified. The application automatically adds 5cm padding to entered dimensions for safety margins.
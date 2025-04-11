# 🧠 Project Prompt

Build a web-based Bento Grid Maker using SvelteKit, Svelte 5, TailwindCSS, and InteractJS, allowing users to drag, resize, and drop content blocks into a customizable grid layout (inspired by modern modular UI frameworks). Users can insert text, images, or videos into each module. Top-level layout only.

---

## ✅ Checklist: Bento Grid Maker – MVP

### 🔧 Setup & Boilerplate

- Initialize SvelteKit project with Svelte 5 support
- Add TailwindCSS with custom config (12-column grid)
- Install and configure @interactjs/interactjs
- Create basic layout page (/editor route)

---

### 🧱 Grid System

- Build the 12-column responsive grid (grid-cols-12)
- Define a BentoCard component
- Support colSpan, rowSpan, x, and y position tracking

---

### 🖱️ InteractJS Integration

- Add draggable support to each BentoCard
- Snap to grid (based on grid size)
- Add resizable support to BentoCard
- Ensure resize respects grid snapping and limits
- Handle z-index while dragging/resizing

---

### 🧩 Content Blocks

- Add dynamic type switching: text, image, video
- Implement content editing for each block:
  - [ ] Text block: contenteditable + autosave
  - Image block: URL or drag-and-drop upload
  - Video block: embed or upload URL
- Render each block based on its type in the grid

---

### 💾 State Management

- Create a modules store with:
  - id, type, x, y, colSpan, rowSpan, content
- Update position and size in the store during drag/resize
- Add undo/redo (basic)
- Save state to localStorage for persistence

---

### 🎨 Visual & Interaction Polish

- Apply Tailwind for visual hierarchy:
  - Rounded corners
  - Aspect ratio control (aspect-[16/9])
  - Hover and active states
  - Optional light/dark mode toggle
  - Add grid background and snap grid indicators

---

### 🎛️ UI Panels

- Add a floating toolbar / sidebar:
  - Add new block (text/image/video)
  - Delete selected block
  - Change layout or background
  - Add layout preview toggle (hide editing UI)

---

### 🧪 Testing & UX

- Handle mobile responsiveness (with limits)
- Prevent overlapping modules
- Smooth drag & resize transitions
- Feedback messages for errors or actions

---

### 🔜 Future Ideas (Post-MVP)

- Export layout to JSON / image / HTML
- Import templates
- Snap lines / smart alignment guides
- Collaborative editing (multiplayer)

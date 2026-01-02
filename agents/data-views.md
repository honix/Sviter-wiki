# Data Views Reference

The wiki supports interactive TSX views and CSV data files.

## File Types

| Extension | Purpose |
|-----------|---------|
| `.md` | Markdown pages |
| `.csv` | Tabular data |
| `.tsx` | Interactive views |

## Creating CSV Files

CSV files store tabular data. Example structure:

```csv
name,email,role
Alice,alice@example.com,admin
Bob,bob@example.com,user
```

## Creating TSX Views

TSX views are React components compiled at runtime. Export a default function component.

### Available Hooks

- `useCSV('file.csv')` - Load and edit CSV data
  - Returns: `{ rows, headers, updateCell, addRow, deleteRow, isLoaded }`
- `usePage('file.md')` - Load any text file content
  - Returns: `{ content, setContent, isLoaded }`
- `useComponent('path.tsx')` - Reuse other TSX components
  - Returns: The component or null if loading

### Available Components

UI components available in scope:
- `Button` - Clickable button with variants
- `Card`, `CardContent`, `CardHeader`, `CardTitle` - Card layout
- `Badge` - Status/count badges
- `Table`, `TableHead`, `TableBody`, `TableRow`, `TableCell`, `TableHeader` - Table layout

### React Hooks

Standard React hooks available:
- `useState`, `useEffect`, `useMemo`, `useCallback`, `memo`, `useRef`

## Examples

See these pages for working examples:

- [examples/simple-view.tsx](examples/simple-view.tsx) - Minimal view with state
- [examples/data-view.tsx](examples/data-view.tsx) - CSV data manipulation
- [examples/kanban.tsx](examples/kanban.tsx) - Kanban board with drag-and-drop
- [components/DataTable.tsx](components/DataTable.tsx) - Reusable component

## Tips

1. Always check `isLoaded` before rendering data
2. CSV cell values are strings - parse numbers with `parseInt()`/`parseFloat()`
3. Use `useComponent` to share UI between views
4. Tailwind CSS classes work for styling

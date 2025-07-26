# Project Gutenberg Recent Books - trmnl Plugin

A trmnl plugin that displays the most recently released or updated books from Project Gutenberg in a clean, e-ink optimized interface.

![Plugin Preview](https://img.shields.io/badge/trmnl-plugin-blue) ![E-ink Optimized](https://img.shields.io/badge/e--ink-optimized-green) ![RSS Feed](https://img.shields.io/badge/data-RSS-orange)

## 📚 Features

- **Real-time Updates**: Displays books posted or updated in the last 24 hours
- **Two-column Layout**: Optimized for full-screen trmnl display
- **Book Covers**: Shows cover images with graceful fallback
- **Rich Metadata**: Displays book ID, language, and truncated titles
- **E-ink Optimized**: Uses trmnl's design system for perfect e-ink rendering

## 🚀 Quick Start

### 1. Install on trmnl

1. Log into your [trmnl account](https://usetrmnl.com)
2. Navigate to **Plugins** → **Private Plugins**
3. Click **Create New Plugin**
4. Copy and paste the template code from `markup.html`
5. Set the data source to RSS feed (see configuration below)

### 2. Configure Data Source

**RSS Feed URL**: `http://www.gutenberg.org/cache/epub/feeds/today.rss`

**Feed Details**:
- Updates: Daily at 2am EST
- Content: Books posted or updated in last 24 hours
- Format: RSS 0.91
- No authentication required

## 🔧 Configuration Options

### Layout Sizes

The plugin is designed for **full-screen layout** but can be adapted:

- **Current**: `view--full` (recommended)
- **Half vertical**: Change to `view--half-vertical`
- **Half horizontal**: Change to `view--half-horizontal`
- **Quadrant**: Change to `view--quadrant`

### Customization

#### Change Number of Books
```liquid
{% for item in rss.channel.item limit: 8 %}  <!-- Show 8 instead of 10 -->
```

#### Modify Title Truncation
```liquid
{{ item.title | strip | truncate: 45 }}  <!-- Increase/decrease character limit -->
```

### RSS Feed Structure

Project Gutenberg's RSS feed follows this structure:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<rss version="0.91">
  <channel>
    <title>Project Gutenberg Recently Posted or Updated EBooks</title>
    <link>https://www.gutenberg.org</link>
    <description>EBooks posted or updated today on Project Gutenberg...</description>
    <lastBuildDate>Sat, 26 Jul 2025 05:51:34 -0400</lastBuildDate>
    
    <item>
      <title>Book Title by Author Name</title>
      <link>https://www.gutenberg.org/ebooks/12345</link>
      <description>Language: English</description>
    </item>
    <!-- More items... -->
  </channel>
</rss>
```

## 🎨 Design System

This plugin uses the [trmnl Design System](https://usetrmnl.com/framework) which provides:

- **E-ink Optimization**: Dithered patterns and 1-bit rendering
- **Consistent Typography**: Standardized text sizes and spacing
- **Responsive Layouts**: Works across different trmnl screen sizes
- **Accessibility**: High contrast and readable fonts

### Key Classes Used

| Class | Purpose |
|-------|---------|
| `layout` | Main container |
| `columns` / `column` | Two-column layout |
| `item` | Individual book container |
| `meta` | Book cover section |
| `content` | Text content section |
| `title--small` | Book title styling |
| `description` | Metadata styling |
| `title_bar` | Header with title and instance |

## 🐛 Troubleshooting

### No Books Showing
- Check if RSS feed is accessible: `http://www.gutenberg.org/cache/epub/feeds/today.rss`
- Verify RSS parsing in trmnl's data source configuration
- Some days may have fewer new releases

### Images Not Loading
- Book covers may not exist for all books
- Plugin includes fallback handling for missing images
- Covers are served from: `https://www.gutenberg.org/cache/epub/{id}/pg{id}.cover.medium.jpg`

## 📄 License

This plugin template is released under the MIT License. Project Gutenberg content is in the public domain.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Test your changes with sample RSS data
4. Submit a pull request

## 🔗 Related Links

- [Project Gutenberg](https://www.gutenberg.org/) - Source of the books
- [trmnl Framework Documentation](https://usetrmnl.com/framework) - Design system docs  
- [trmnl Plugin Marketplace](https://usetrmnl.com/plugins) - Browse other plugins
- [Project Gutenberg RSS Feeds](https://www.gutenberg.org/ebooks/feeds.html) - Other available feeds

## 📊 Data Sources

### Primary
- **RSS Feed**: `http://www.gutenberg.org/cache/epub/feeds/today.rss`
- **Update Schedule**: Nightly regeneration
- **Content**: Last 24 hours of activity

### Alternative (for reference)
- **Gutendx API**: `https://gutendx.com/books/?sort=descending`
- **Format**: JSON
- **Sorting**: By Project Gutenberg ID (newest first)

---

**Made for trmnl** | Built with ❤️ for the e-ink community

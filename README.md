# Space Research Laboratory Website

A dynamic and interactive space-themed research lab website built with Jekyll, featuring a modern design with the color scheme #00549A (deep blue) and #FFCD4D (gold).

## Features

- **Space-themed Design**: Beautiful space-inspired design with animated stars and cosmic elements
- **Responsive Layout**: Fully responsive design that works on all devices
- **Interactive Elements**: Hover effects, animations, and dynamic content
- **Search Functionality**: Search and filter publications by year and content
- **Modern UI/UX**: Clean, professional interface with excellent user experience
- **Jekyll-powered**: Easy to maintain and update content

## Pages

1. **Home** (`/`) - Research overview and featured projects
2. **Team** (`/team/`) - Lab members and Principal Investigator
3. **Publications** (`/publications/`) - Research publications with search and filter
4. **Research** (`/research/`) - Detailed research areas and current projects

## Color Scheme

- **Primary Color**: #00549A (Deep Blue)
- **Secondary Color**: #FFCD4D (Gold)
- **Supporting Colors**: Various shades of blue and gray

## Prerequisites

Before you begin, ensure you have the following installed:
- Ruby (version 2.6 or higher)
- RubyGems
- GCC and Make

## Installation

1. **Clone or download this repository**
   ```bash
   git clone <repository-url>
   cd XDLAB
   ```

2. **Install Jekyll and dependencies**
   ```bash
   bundle install
   ```

3. **Serve the website locally**
   ```bash
   bundle exec jekyll serve
   ```

4. **Access the website**
   Open your browser and go to `http://localhost:4000`

## Development

### File Structure
```
XDLAB/
├── _config.yml          # Jekyll configuration
├── _layouts/            # Layout templates
│   ├── default.html     # Main layout
│   └── page.html        # Page layout
├── assets/              # Static assets
│   ├── css/
│   │   └── main.css     # Main stylesheet
│   └── js/
│       └── main.js      # JavaScript functionality
├── team/                # Team page
│   └── index.html
├── publications/        # Publications page
│   └── index.html
├── research/           # Research page
│   └── index.html
├── index.html          # Home page
├── Gemfile             # Ruby dependencies
└── README.md           # This file
```

### Customization

#### Adding New Team Members
1. Edit `team/index.html`
2. Add new team member cards following the existing structure
3. Update placeholder images with actual photos

#### Adding Publications
1. Edit `publications/index.html`
2. Add new publication items following the existing structure
3. Include proper metadata (year, category, authors, etc.)

#### Modifying Colors
1. Edit `assets/css/main.css`
2. Update CSS variables in the `:root` selector:
   ```css
   :root {
       --primary-color: #00549A;
       --secondary-color: #FFCD4D;
       /* ... other colors */
   }
   ```

#### Adding New Pages
1. Create a new directory for the page
2. Add an `index.html` file with the page layout
3. Update navigation in `_layouts/default.html`

### Content Management

The website uses Jekyll's front matter for content management. Each page has metadata at the top:

```yaml
---
layout: page
title: Page Title
subtitle: Page Subtitle
---
```

## Features in Detail

### Interactive Elements
- **Hover Effects**: Cards and buttons have smooth hover animations
- **Mobile Navigation**: Responsive hamburger menu for mobile devices
- **Search & Filter**: Publications can be searched and filtered by year
- **Smooth Scrolling**: Navigation links scroll smoothly to sections
- **Back to Top**: Animated rocket button to return to top of page

### Animations
- **Floating Stars**: Animated star background in hero section
- **Rocket Animation**: Animated rocket icon in navigation
- **Fade-in Effects**: Elements animate in as you scroll
- **Particle Effects**: Floating particles in the background

### Responsive Design
- **Mobile-first**: Optimized for mobile devices
- **Flexible Grid**: CSS Grid and Flexbox for responsive layouts
- **Touch-friendly**: Large touch targets for mobile interaction

## Deployment

### GitHub Pages
1. Push your code to a GitHub repository
2. Enable GitHub Pages in repository settings
3. Select the branch you want to deploy from

### Netlify
1. Connect your GitHub repository to Netlify
2. Set build command: `bundle exec jekyll build`
3. Set publish directory: `_site`

### Other Hosting
1. Build the site: `bundle exec jekyll build`
2. Upload the `_site` directory to your web server

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Performance

The website is optimized for performance with:
- Minified CSS and JavaScript
- Optimized images and icons
- Efficient animations using CSS transforms
- Lazy loading for better page load times

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally with `bundle exec jekyll serve`
5. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

For questions or issues:
1. Check the [Jekyll documentation](https://jekyllrb.com/docs/)
2. Review the code comments for implementation details
3. Open an issue in the repository

## Credits

- **Fonts**: Google Fonts (Orbitron, Roboto)
- **Icons**: Font Awesome
- **Design**: Custom space-themed design
- **Framework**: Jekyll static site generator

---

**Space Research Laboratory** - Exploring the frontiers of space science and technology. 
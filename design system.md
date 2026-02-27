
You need a **UI Contract Specification**.

A deterministic layer that sits between:

- Design intent
- Component library (e.g. shadcn)
- Generated UI
- Engineering implementation

Treat UI like an API surface.

Components of our design system
- Design Tokens (primitive layer)
- Semantic Tokens (intent layer)
- Component Contracts (behavior layer)
- Layout Constraints (composition layer)
- State Matrix (interaction layer)

AI must consume tokens and component contracts only.

design tokens example
Enforce via lint rules
```json
{
  "color": {
    "neutral": {
      "0": "#FFFFFF",
      "100": "#F5F5F5",
      "900": "#111111"
    },
    "brand": {
      "500": "#3A5FFF"
    },
    "danger": {
      "500": "#E5484D"
    }
  },
  "radius": {
    "sm": "4px",
    "md": "8px",
    "lg": "12px"
  },
  "space": {
    "1": "4px",
    "2": "8px",
    "3": "12px",
    "4": "16px"
  }
}
```


You define semantic mapping:

```json
{  
  "button": {  
    "primary": {  
      "bg": "color.brand.500",  
      "text": "color.neutral.0",  
      "radius": "radius.md",  
      "paddingX": "space.4",  
      "paddingY": "space.2"  
    }  
  }  
}
```



Create ESLint rule:
- Ban raw color utilities
- Ban arbitrary Tailwind values
- Ban inline styles


/design-system folder

Design System = UI Kernel  
shadcn = Rendering Runtime  
AI = Code Producer constrained by kernel  
ESLint + TS = Enforcement Layer



---

select our colors, fonts


design system = **style guide** + **a component library** + **pattern library**.

**Style guides** contain specific implementation guidelines, visual references, and [design principles](https://www.nngroup.com/videos/design-principles-101/) for creating interfaces or other design deliverables. The most-common style guides tend to focus on branding (colors, typography, trademarks, logos, and print media), but style guides also offer guidance on content (such as [tone of voice](https://www.nngroup.com/articles/tone-of-voice-dimensions/) and language recommendations) and visual- and interaction-design standards (also known as [front-end style guides](https://www.nngroup.com/articles/front-end-style-guides/)).

while **pattern libraries** feature collections of UI-element groupings or layouts. like bridjr maybe
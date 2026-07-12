### import { Metadata } from "next";
Its a built in feature which allow us to define and manage SEO related and social media related information for your pages and layout.

```
export const metadata: Metadata = {
  title: "About | My Website",
  description: "Learn more about our company and mission.",
};
```
- next.js automatically injects this into the head element.
# Encoded Empires: A Digital Exploration of Royal Correspondence

## Overview

This project is a digital humanities exploration of four medieval letters written by Constance of Hungary, queen consort of Bohemia in the 13th century. Using text encoding (TEI/XML), Voyant Tools, and Omeka Classic paired with the Exhibit Builder plugin, the project analyzes the rhetoric of royal correspondence, highlighting themes of authority, piety, and female political influence. This exhibit can be viewed on my website, [theroyalarchives.org](https://www.theroyalarchives.org/). Deployed and hosted on a GCP VM.

## Purpose

This project set out to explore how digital tools can be applied to the study of historical correspondence. By combining text encoding, metadata, and visualization methods, the aim was to uncover new insights into royal women's political and cultural influence. The project serves both as a case study in digital humanities practice and as a demonstration of technical skills in building, managing, and presenting a digital archive.

## Methods

This project used a combination of humanities-centered and technical approaches:

- **TEI/XML** was employed to encode the letters, highlighting key people, places, and institutions.

- **Voyant** Tools provided text analysis for word frequency, trends, and context. Both per-letter and corpus-wide analyses were done.

- **Dublin Core metadata** structured the descriptive information for each item.

- **Omeka Classic** hosted the digital collection and exhibited both the primary sources and analytical findings.

Together, these tools created a workflow that combined careful text preparation with computational analysis and public presentation.

## Repository Structure

├── docs/ ----------------- Technical notes, VM settings and setup instructions, db.ini template, license

├── plain-text/ ------------ Plain text versions of Constance's letters

├── tei/ -------------------- Encoded XML versions of Constance's letters

├── voyant/ --------------- Voyant Analysis screenshots

├── .gitignore ------------- The .gitignore for this project

└── README.md ---------- Project overview

## Key Findings

The analysis revealed recurring rhetorical patterns and thematic emphases across the letters. For example, the encoded references to institutions highlighted the Queen's role in mediating between religious and political entities. Text analysis visualizations showed the persistence of place-based language, emphasizing geographic power and extending influence across regions. These findings illustrate the letters' value as both historical documents and artifacts of political strategy.

## Why It Matters

This project shows how digital methods can enrich the study of historical, and in this case, medieval texts. By combining humanistic interpretation with computational tools, it provides new insights into the rhetorical strategies of royal women and expands access to historical sources through a digital exhibit. For scholars, students, and the public, it illustrates how digital technologies can bridge the gap between historical sources and contemporary understanding.

## Skills Demonstrated

- Web deployment on cloud VMs (Google Cloud, Laragon for local testing).

- Database management in local and cloud environments (MySQL/MariaDB).

- Server and domain configuration (Apache, PHP, SSL with Let's Encrypt, Cloudflare).

- SSH utilization and cloud file management.

- Digital Humanities methods (TEI/XML, metadata standards, text analysis).

## Installation Guides and Links

If you would like to give Omeka Classic and exhibit building a try yourself:

- [Omeka Classic](https://omeka.org/classic/)

- [Omeka Classic Installation Guide](https://omeka.org/classic/docs/Installation/Installing/)

- [Laragon](https://laragon.org/) (for local development/sandbox testing)

- [Exhibit Builder Plugin](https://omeka.org/classic/plugins/ExhibitBuilder/) (for Omeka)

- [ImageMagick](https://imagemagick.org/) (for derivative images/thumbnails in Omeka)

## Tags

Digital Humanities, Omeka Classic, Laragon, ImageMagick, TEI, Voyant Tools, Dublin Core, Metadata, Cloud Deployment, Cloud Hosting, Linux, Apache, MySQL, MariaDB, PHP
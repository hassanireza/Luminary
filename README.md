<div align="center">

# Luminary

### A refined Django image-sharing website with an editorial gallery feed, polished upload flow, and luxury dark-gold interface.

![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=111111)

</div>

---

## Overview

**Luminary** is a Django-powered visual sharing application built around a simple, elegant publishing loop: upload an image, add a short caption, and browse moments through a responsive gallery feed.

The project combines classic Django architecture with a highly designed front end. Its interface uses a cinematic dark palette, gold gradients, serif typography, responsive image cards, drag-and-drop upload interactions, and polished detail pages to create a premium social-gallery experience.

It is intentionally compact, readable, and portfolio-ready: a strong foundation for an image feed, visual journal, inspiration board, creator portfolio, or lightweight social posting product.

---

## Interface

```text
Luminary

Share a new moment.
Upload an image and give it a caption worth remembering.
```

The application includes three main user-facing surfaces:

- **Home feed** - a responsive image grid ordered by newest post first
- **Post detail** - an immersive image view with caption metadata and download action
- **New post** - a custom upload page with image preview, caption input, and publish state

---

## Features

- **Image post model** with caption text and uploaded media
- **Responsive gallery feed** using square image cards and hover overlays
- **Post detail pages** for individual image moments
- **Image upload form** with multipart handling
- **Drag-and-drop upload UI** with client-side preview
- **Django message feedback** after successful publishing
- **Media file serving in development**
- **Class-based Django views** for clean page structure
- **Custom design system** using CSS variables, gradients, and typography tokens
- **Mobile-conscious layouts** with adaptive navigation, cards, and forms
- **Thumbnail support** through `sorl-thumbnail`

---

## Tech Stack

| Area | Technology |
| --- | --- |
| Backend | Django |
| Language | Python |
| Database | SQLite |
| Views | Django class-based views |
| Forms | Django forms |
| Templates | Django Template Language |
| Media | Django media uploads |
| Images | `sorl-thumbnail` |
| Frontend | HTML, CSS, vanilla JavaScript |
| Typography | Google Fonts: Cormorant Garamond, DM Sans |

---

## Application Flow

```text
Visitor
  |
  |-- opens home feed
  |     `-- sees newest image posts first
  |
  |-- clicks a post
  |     `-- opens detail page with caption and image actions
  |
  `-- creates a new post
        |-- selects or drops an image
        |-- previews the file
        |-- writes a caption
        `-- publishes to the feed
```

---

## Project Structure

```text
.
|-- manage.py
|-- feed/
|   |-- admin.py
|   |-- apps.py
|   |-- forms.py
|   |-- models.py
|   |-- urls.py
|   |-- views.py
|   `-- migrations/
|       |-- 0001_initial.py
|       `-- 0002_post_image.py
|-- mysite/
|   |-- asgi.py
|   |-- settings.py
|   |-- urls.py
|   `-- wsgi.py
`-- templates/
    |-- base.html
    |-- home.html
    |-- detail.html
    `-- new_post.html
```

---

## Core Model

Luminary is centered around a compact `Post` model:

```python
class Post(models.Model):
    text = models.CharField(max_length=140, blank=False, null=False)
    image = ImageField()

    def __str__(self):
        return self.text
```

Each post stores:

- A short caption
- An uploaded image
- A readable string representation for the Django admin and shell

---

## Routes

| URL | View | Purpose |
| --- | --- | --- |
| `/` | `HomePageView` | Displays the gallery feed |
| `/detail/<int:pk>/` | `PostDetailView` | Displays one image post |
| `/post/` | `AddPostView` | Handles new image uploads |
| `/admin/` | Django Admin | Project administration |

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/your-username/luminary.git
cd luminary
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it:

```bash
# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install django sorl-thumbnail pillow
```

If you maintain a dependency file, add:

```text
Django
sorl-thumbnail
Pillow
```

### 4. Apply migrations

```bash
python manage.py migrate
```

### 5. Create an admin user

```bash
python manage.py createsuperuser
```

### 6. Run the development server

```bash
python manage.py runserver
```

Open:

```text
http://127.0.0.1:8000/
```

---

## Media Uploads

In development, uploaded images are stored under:

```text
media/
```

The project serves media files while `DEBUG = True` through:

```python
urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

For production, serve media through object storage or a dedicated media server.

Recommended production options:

- Amazon S3
- Cloudflare R2
- DigitalOcean Spaces
- Google Cloud Storage
- Nginx-backed media storage

---

## Design System

Luminary uses a bespoke visual language built for a premium image-sharing experience.

### Visual Direction

- Deep black and warm charcoal surfaces
- Gold gradient accents for primary actions and brand identity
- Large serif display type for an editorial tone
- Soft borders, elevated cards, and subtle glow effects
- Full-bleed image moments with refined metadata panels

### UI Patterns

- Sticky glass-style navigation
- Primary and ghost button variants
- Responsive gallery cards
- Hover overlays for image discovery
- Toast-style Django messages
- Drag-and-drop upload zone
- Mobile-first spacing refinements

---

## Production Checklist

Before deploying publicly, update the following:

- Move `SECRET_KEY` into an environment variable
- Set `DEBUG = False`
- Configure `ALLOWED_HOSTS`
- Use a production database such as PostgreSQL
- Configure static file collection and hosting
- Configure production media storage
- Add file size and file type validation for uploads
- Add authentication if posting should be restricted
- Add tests for model creation, upload flow, and view responses

---

## Suggested Enhancements

Luminary is a clean base for a larger product. Strong next features include:

- User accounts and author profiles
- Like and save interactions
- Caption search
- Tags or collections
- Image moderation tools
- Infinite scroll or pagination
- Cloud media storage
- Post timestamps
- Profile galleries
- API endpoints for a future mobile or SPA client

---

## Quality Notes

This project currently keeps the application intentionally small and understandable. The main production-sensitive areas are configuration, media validation, and deployment hardening. Those should be addressed before using the project as a public multi-user platform.

---

<div align="center">

**Luminary**  
Share visual moments through a Django experience that feels crafted, calm, and production-minded.

</div>

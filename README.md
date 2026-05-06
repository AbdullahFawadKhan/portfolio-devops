# MTG Pro Decklist - DevOps Pipeline

## Team Members
- Abdullah Fawad Khan      2024038


## Project Description
A containerized web application that allows an MTG (Magic: The Gathering) professional player to publicly display and update their tournament decklist and sideboard. Changes go live in under 3 minutes via CI/CD pipeline.

## Real-World Use Case
Professional MTG players need to share their current decklists with:
- Tournament organizers for deck checks
- Opponents preparing for matches  
- Fans and content creators
- Teammates for collaboration

This solution provides version-controlled, automated deployment of decklists without requiring any technical knowledge after initial setup.

## Architecture

| Component | Technology |
|-----------|------------|
| Version Control | Git & GitHub |
| Containerization | Docker (Nginx Alpine) |
| CI/CD | GitHub Actions |
| Cloud Platform | AWS EC2 (Ubuntu 26.04, t3.micro) |
| Infrastructure (Optional) | Terraform |

## DevOps Pipeline Flow
1. Edit `index.html` locally (update decklist cards)
2. `git push` to GitHub `main` branch
3. GitHub Actions automatically triggers:
   - Logs into Docker Hub
   - Builds new Docker image
   - Pushes image to registry
   - SSHs into AWS EC2
   - Pulls latest image and restarts container
4. Updated decklist is live on public URL

## Live Demo
http://16.170.255.187

## How to Update Decklist
```bash
git pull
# Edit index.html (change card names/quantities)
git add .
git commit -m "update sideboard for upcoming tournament"
git push
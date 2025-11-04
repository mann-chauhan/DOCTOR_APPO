# Doctor Appointment System - Production Deployment Guide

## Pre-Deployment Checklist

### Backend
- [ ] Set secure JWT_SECRET in production .env
- [ ] Use MongoDB Atlas or secure MongoDB instance
- [ ] Enable CORS for production domain only
- [ ] Set NODE_ENV=production
- [ ] Remove console.logs or use proper logging
- [ ] Set up proper error logging
- [ ] Configure rate limiting
- [ ] Set up HTTPS
- [ ] Review and secure API endpoints

### Frontend
- [ ] Update API base URL for production
- [ ] Build production bundle: `npm run build`
- [ ] Test production build locally
- [ ] Set up proper error boundaries
- [ ] Optimize images and assets
- [ ] Enable service worker (optional)
- [ ] Set up analytics (optional)

## Deployment Options

### Option 1: Heroku

#### Backend Deployment
1. Install Heroku CLI
2. Create Heroku app: `heroku create doctor-appointment-api`
3. Set environment variables:
   ```bash
   heroku config:set MONGODB_URI=your_mongodb_uri
   heroku config:set JWT_SECRET=your_secret_key
   heroku config:set NODE_ENV=production
   ```
4. Deploy: `git push heroku main`

#### Frontend Deployment
1. Update `client/package.json` proxy to production API URL
2. Build: `cd client && npm run build`
3. Serve static files or deploy to Netlify/Vercel

### Option 2: AWS/EC2

1. Set up EC2 instance
2. Install Node.js and MongoDB
3. Clone repository
4. Set up PM2: `pm2 start server/server.js`
5. Configure Nginx as reverse proxy
6. Set up SSL certificate

### Option 3: Docker

Create `Dockerfile`:
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "run", "server"]
```

## Environment Variables

### Production .env
```env
NODE_ENV=production
MONGODB_URI=your_production_mongodb_uri
JWT_SECRET=strong_random_secret_key_here
PORT=5000
```

## Security Best Practices

1. **Never commit .env files**
2. **Use strong JWT secrets**
3. **Enable HTTPS**
4. **Implement rate limiting**
5. **Validate all inputs**
6. **Sanitize user inputs**
7. **Use parameterized queries**
8. **Set secure headers**
9. **Regular security updates**

## Monitoring

- Set up error tracking (Sentry, etc.)
- Monitor API response times
- Set up database backups
- Monitor server resources
- Set up uptime monitoring

## Backup Strategy

- Regular MongoDB backups
- Database backup before updates
- Version control for code
- Document all changes

## Post-Deployment

1. Test all features
2. Verify SSL certificate
3. Check error logs
4. Monitor performance
5. Set up alerts


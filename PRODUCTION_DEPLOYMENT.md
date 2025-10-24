# Production Deployment Guide

This guide will help you deploy your ChatKit application to production safely and securely.

## Prerequisites

1. **OpenAI API Key**: Get from [OpenAI API Keys](https://platform.openai.com/api-keys)
2. **Workflow ID**: Get from [Agent Builder](https://platform.openai.com/agent-builder) after clicking "Publish"
3. **Domain**: Your production domain (e.g., `https://yourdomain.com`)

## Environment Variables

Create a `.env.local` file with the following variables:

```bash
# Required
OPENAI_API_KEY=your_openai_api_key_here
NEXT_PUBLIC_CHATKIT_WORKFLOW_ID=wf_your_workflow_id_here

# Production Security (Required)
ALLOWED_ORIGINS=https://yourdomain.com,https://www.yourdomain.com

# Optional
CHATKIT_API_BASE=https://api.openai.com
SESSION_DOMAIN=yourdomain.com
```

## Security Configuration

### 1. Domain Allowlist
Before deploying, add your domain to the [Domain allowlist](https://platform.openai.com/settings/organization/security/domain-allowlist) on your OpenAI dashboard.

### 2. CORS Configuration
The application is configured to restrict CORS to your specified domains in production. Update `ALLOWED_ORIGINS` with your actual domains.

### 3. Security Headers
The application includes security headers:
- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: DENY`
- `X-XSS-Protection: 1; mode=block`

## Build and Deploy

### 1. Build the Application
```bash
npm run build
```

### 2. Start Production Server
```bash
npm start
```

### 3. Verify Deployment
- Test the application at your domain
- Verify ChatKit loads correctly
- Check that API endpoints respond properly
- Test file upload functionality if enabled

## Deployment Platforms

### Vercel (Recommended)
1. Connect your repository to Vercel
2. Add environment variables in Vercel dashboard
3. Deploy automatically on push

### Other Platforms
- **Netlify**: Use `npm run build` and deploy the `.next` folder
- **Railway**: Use `npm start` after build
- **Docker**: Create a Dockerfile with Node.js and run `npm start`

## Monitoring and Maintenance

### 1. Logs
Monitor application logs for:
- API errors
- Session creation failures
- Rate limiting issues

### 2. Performance
- Monitor response times
- Check memory usage
- Optimize if needed

### 3. Security
- Regularly update dependencies
- Monitor for security vulnerabilities
- Review access logs

## Troubleshooting

### Common Issues

1. **CORS Errors**: Verify `ALLOWED_ORIGINS` includes your domain
2. **Session Creation Fails**: Check `OPENAI_API_KEY` and `NEXT_PUBLIC_CHATKIT_WORKFLOW_ID`
3. **Domain Not Allowed**: Add your domain to OpenAI's allowlist
4. **Build Errors**: Ensure all environment variables are set

### Support
- Check OpenAI documentation for ChatKit issues
- Review Next.js deployment guides
- Monitor application logs for detailed error messages

## Best Practices

1. **Environment Variables**: Never commit `.env.local` to version control
2. **API Keys**: Use environment-specific keys for production
3. **Monitoring**: Set up error tracking and performance monitoring
4. **Backups**: Regular backups of your configuration
5. **Updates**: Keep dependencies updated for security patches

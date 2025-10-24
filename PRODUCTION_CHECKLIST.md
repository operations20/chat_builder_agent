# Production Deployment Checklist

## ✅ Pre-Deployment Checklist

### Environment Configuration
- [ ] Set `OPENAI_API_KEY` environment variable
- [ ] Set `NEXT_PUBLIC_CHATKIT_WORKFLOW_ID` environment variable  
- [ ] Configure `ALLOWED_ORIGINS` for your production domain
- [ ] Optional: Set `CHATKIT_API_BASE` if using custom endpoint
- [ ] Optional: Set `SESSION_DOMAIN` for cookie configuration

### Security Configuration
- [ ] Add your domain to OpenAI's [Domain allowlist](https://platform.openai.com/settings/organization/security/domain-allowlist)
- [ ] Verify CORS settings match your production domain
- [ ] Ensure HTTPS is enabled in production
- [ ] Review and update security headers as needed

### Build and Testing
- [ ] Run `npm run build` successfully
- [ ] Test production build locally with `npm start`
- [ ] Verify ChatKit loads correctly
- [ ] Test API endpoint functionality
- [ ] Test file upload if enabled
- [ ] Verify error handling works properly

### Deployment Platform Setup
- [ ] Configure environment variables on your deployment platform
- [ ] Set up custom domain (if applicable)
- [ ] Configure SSL/TLS certificates
- [ ] Set up monitoring and logging

## ✅ Post-Deployment Verification

### Functionality Tests
- [ ] Application loads at your production URL
- [ ] ChatKit interface appears correctly
- [ ] Can create new chat sessions
- [ ] API endpoints respond correctly
- [ ] Error handling works as expected
- [ ] File uploads work (if enabled)

### Security Verification
- [ ] CORS headers are properly configured
- [ ] Security headers are present
- [ ] No sensitive information in client-side code
- [ ] API keys are not exposed
- [ ] Domain allowlist is configured

### Performance Checks
- [ ] Page load times are acceptable
- [ ] API response times are reasonable
- [ ] No console errors in browser
- [ ] Memory usage is stable
- [ ] No memory leaks detected

## 🔧 Troubleshooting Common Issues

### Build Issues
- **Error**: Missing environment variables
  - **Solution**: Ensure all required environment variables are set
- **Error**: TypeScript compilation errors
  - **Solution**: Run `npm run lint` and fix any issues

### Runtime Issues
- **Error**: CORS issues
  - **Solution**: Verify `ALLOWED_ORIGINS` includes your domain
- **Error**: Session creation fails
  - **Solution**: Check API key and workflow ID configuration
- **Error**: Domain not allowed
  - **Solution**: Add domain to OpenAI allowlist

### Performance Issues
- **Issue**: Slow page loads
  - **Solution**: Check network requests, optimize images, enable compression
- **Issue**: High memory usage
  - **Solution**: Monitor for memory leaks, optimize code

## 📊 Monitoring Recommendations

### Application Monitoring
- Set up error tracking (e.g., Sentry, LogRocket)
- Monitor API response times
- Track user sessions and errors
- Monitor memory and CPU usage

### Security Monitoring
- Monitor for unusual API usage patterns
- Track failed authentication attempts
- Monitor for potential security vulnerabilities
- Regular security audits

## 🚀 Production Optimization Tips

1. **Enable Compression**: Already configured in `next.config.ts`
2. **Use CDN**: Consider using a CDN for static assets
3. **Monitor Performance**: Set up performance monitoring
4. **Regular Updates**: Keep dependencies updated
5. **Backup Configuration**: Keep environment configuration backed up
6. **Documentation**: Maintain deployment documentation

## 📞 Support Resources

- [Next.js Deployment Documentation](https://nextjs.org/docs/deployment)
- [OpenAI ChatKit Documentation](https://openai.github.io/chatkit-js/)
- [OpenAI Platform Documentation](https://platform.openai.com/docs)
- [Vercel Deployment Guide](https://vercel.com/docs) (if using Vercel)

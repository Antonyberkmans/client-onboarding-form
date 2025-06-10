# Client Onboarding Form

A professional, responsive client onboarding form that automatically collects and processes client information through automated workflows.

## 🚀 Live Demo

Visit the live form: [https://yourusername.github.io/client-onboarding-form/](https://yourusername.github.io/client-onboarding-form/)

*Replace `yourusername` with your actual GitHub username*

## ✨ Features

- **Responsive Design** - Works perfectly on desktop, tablet, and mobile devices
- **Professional UI** - Clean black & white theme with smooth animations
- **Form Validation** - Real-time validation with user-friendly error messages
- **Auto-formatting** - Phone numbers automatically formatted as user types
- **Loading States** - Visual feedback during form submission
- **Success/Error Handling** - Clear confirmation messages for users
- **Automated Processing** - Integrates with n8n workflows for automatic data processing
- **Database Storage** - Client data automatically stored in Supabase database

## 📋 Form Fields

The form collects the following client information:

- **Company Name** *(required)*
- **Contact Name** *(required)*
- **Email Address** *(required)*
- **Phone Number** *(optional)*
- **Website URL** *(optional)*
- **Industry** *(optional)*
- **Project Budget** *(optional)*
- **Project Goals & Description** *(optional)*

## 🛠️ Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Hosting**: GitHub Pages
- **Backend**: n8n (workflow automation)
- **Database**: Supabase (PostgreSQL)
- **Styling**: Custom CSS with animations and responsive design

## ⚙️ Setup Instructions

### Prerequisites

1. **n8n instance** (cloud or self-hosted)
2. **Supabase account** and database
3. **GitHub account** for hosting

### Quick Setup

1. **Clone this repository**
   ```bash
   git clone https://github.com/yourusername/client-onboarding-form.git
   cd client-onboarding-form
   ```

2. **Configure the webhook URL**
   - Open `index.html`
   - Find line: `const WEBHOOK_URL = 'YOUR_N8N_WEBHOOK_URL_HERE';`
   - Replace with your actual n8n webhook URL

3. **Deploy to GitHub Pages**
   - Push changes to your repository
   - Enable GitHub Pages in repository settings
   - Your form will be live at: `https://yourusername.github.io/client-onboarding-form/`

### Detailed Configuration

#### n8n Workflow Setup

1. Create a new n8n workflow with:
   - **Webhook trigger** (accepts POST requests)
   - **Supabase node** (for database storage)

2. Configure webhook to accept JSON data with these fields:
   ```json
   {
     "company_name": "string",
     "contact_name": "string", 
     "email": "string",
     "phone": "string",
     "website": "string",
     "industry": "string",
     "budget": "string",
     "goals": "string"
   }
   ```

#### Supabase Database Setup

Create a `clients` table with this structure:

```sql
CREATE TABLE clients (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  created_at TIMESTAMPTZ DEFAULT NOW(),
  company_name TEXT NOT NULL,
  contact_name TEXT NOT NULL,
  email TEXT UNIQUE NOT NULL,
  phone TEXT,
  website TEXT,
  industry TEXT,
  budget TEXT,
  goals TEXT
);

-- Disable RLS for n8n access
ALTER TABLE clients DISABLE ROW LEVEL SECURITY;
```

## 🔧 Customization

### Styling

The form uses a clean black & white theme. To customize:

- **Colors**: Modify CSS variables in the `<style>` section
- **Fonts**: Update `font-family` properties
- **Layout**: Adjust grid layouts in `.form-row` class
- **Animations**: Modify `@keyframes` rules

### Form Fields

To add or modify form fields:

1. Add HTML input elements in the form
2. Update the JavaScript form data collection
3. Ensure your n8n workflow accepts the new fields
4. Update the database schema if needed

### Validation

Form validation can be customized in the JavaScript section:

```javascript
// Add custom validation rules
inputs.forEach(input => {
    input.addEventListener('blur', function() {
        // Your custom validation logic here
    });
});
```

## 📱 Responsive Design

The form is fully responsive and optimized for:

- **Desktop** (1200px+)
- **Tablet** (768px - 1199px)
- **Mobile** (320px - 767px)

## 🔒 Security Features

- **HTTPS** enabled through GitHub Pages
- **Input validation** and sanitization
- **CORS-friendly** webhook integration
- **No sensitive data** stored in frontend code

## 📊 Analytics & Monitoring

To track form submissions, you can:

1. Add Google Analytics tracking
2. Implement custom event tracking
3. Monitor n8n workflow executions
4. Set up Supabase database monitoring

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 📞 Support

For questions or support:

- **GitHub Issues**: [Create an issue](https://github.com/yourusername/client-onboarding-form/issues)
- **Email**: your-email@example.com
- **Documentation**: Check the [Wiki](https://github.com/yourusername/client-onboarding-form/wiki)

## 🚀 Deployment Status

- **Status**: ✅ Live
- **Last Updated**: [Date]
- **Version**: 1.0.0
- **Uptime**: 99.9%

---

**Built with ❤️ for seamless client onboarding**

## 📈 Roadmap

- [ ] Add file upload capability
- [ ] Implement multi-step form wizard
- [ ] Add email confirmation
- [ ] Create admin dashboard
- [ ] Add export functionality
- [ ] Implement form analytics

---

*This form is part of an automated client onboarding system that streamlines data collection and processing.*

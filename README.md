# 🧬 TB-Findings: Natural Language Analysis of Global Tuberculosis Burden

This project uses [PromptQL](https://promptql.io) to enable natural language querying of global tuberculosis (TB) burden data from WHO. Users can explore incidence, prevalence, mortality, and TB-HIV co-infection rates across countries and years without writing SQL.

---

## 📂 Dataset

- **Source:** WHO Global Tuberculosis Report
- **File:** `TB_Burden_Country.csv`
- **Coverage:** Country-level TB metrics from 1990 to 2022
- **Metrics include:**
  - TB incidence and prevalence
  - Mortality (with and without HIV)
  - HIV-TB co-infection
  - Case detection rates

---

## 🛠️ Getting Started

### 1. Clone the Repository via SSH

If you haven’t set up your SSH key yet:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
pbcopy < ~/.ssh/id_rsa.pub  # Mac: copies the key to clipboard
```
Then add the SSH key to your GitHub account:
GitHub SSH Key Setup
Now clone the project:
```
git clone git@github.com:<your-username>/TB-Findings.git
cd TB-Findings
```

###2. Install DDN CLI and Docker

Install DDN CLI and Docker Compose:
```
curl -L https://graphql-engine-cdn.hasura.io/ddn/cli/v4/get.sh | bash
ddn doctor 
```

###3. Add Your CSV

Place your dataset into:
```
app/connector/csv/csv_files/TB_Burden_Country.csv
```

###4. Launch PromptQL
```
ddn connector introspect csv
ddn model add csv "*"
ddn supergraph build local
ddn project init
ddn run docker-start
ddn console --local
```

###💬 Example Questions You Can Ask
```
“Which country had the highest TB incidence in 2022?”
“List countries with more than 10,000 TB-related deaths.”
“Show TB-HIV co-infection trends for South Africa.”
“What is the average case detection rate across all countries?”
PromptQL will translate these into structured queries and display results with explanations.
```

###📊 Project Goals

- Democratize access to global TB data through natural language.
- Enable public health researchers and analysts to extract insights without coding.
- Lay the groundwork for future disease burden dashboards and predictive analytics.

###🔗 Resources
- PromptQL Docs
- Hasura DDN
- WHO TB Data
- GitHub SSH Docs

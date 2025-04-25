import pandas as pd
import numpy as np

# Set seed for reproducibility
np.random.seed(42)
n_samples = 300

# Generate a synthetic dataset for placement prediction
data = {
    "CGPA": np.round(np.random.uniform(6.0, 10.0, size=n_samples), 2),
    "Internships": np.random.randint(0, 3, size=n_samples),
    "Certifications": np.random.randint(0, 5, size=n_samples),
    "Projects": np.random.randint(1, 4, size=n_samples),
    "Hackathons": np.random.randint(0, 5, size=n_samples),
    "Communication Score": np.round(np.random.uniform(1, 10, size=n_samples), 1),
    "Domain": np.random.choice(["AI/ML", "Web Dev", "Cybersecurity", "Data Science"], size=n_samples)
}

# Placement status based on a weighted combination
placement_score = (
    0.3 * data["CGPA"] +
    0.1 * data["Internships"] +
    0.1 * data["Certifications"] +
    0.15 * data["Projects"] +
    0.1 * data["Hackathons"] +
    0.25 * data["Communication Score"]
)

placement_prob = (placement_score - placement_score.min()) / (placement_score.max() - placement_score.min())
placement_status = np.where(np.random.rand(n_samples) < placement_prob, "Placed", "Not Placed")

# Salary package only for placed students
salary = np.where(
    placement_status == "Placed",
    np.round(np.random.normal(4, 1.5, size=n_samples).clip(2, 12), 2),
    0.0
)

df_placement = pd.DataFrame(data)
df_placement["Placement Status"] = placement_status
df_placement["Salary (LPA)"] = salary

df_placement.head()import pandas as pd
import numpy as np

# Set seed for reproducibility
np.random.seed(42)
n_samples = 300

# Generate a synthetic dataset for placement prediction
data = {
    "CGPA": np.round(np.random.uniform(6.0, 10.0, size=n_samples), 2),
    "Internships": np.random.randint(0, 3, size=n_samples),
    "Certifications": np.random.randint(0, 5, size=n_samples),
    "Projects": np.random.randint(1, 4, size=n_samples),
    "Hackathons": np.random.randint(0, 5, size=n_samples),
    "Communication Score": np.round(np.random.uniform(1, 10, size=n_samples), 1),
    "Domain": np.random.choice(["AI/ML", "Web Dev", "Cybersecurity", "Data Science"], size=n_samples)
}

# Placement status based on a weighted combination
placement_score = (
    0.3 * data["CGPA"] +
    0.1 * data["Internships"] +
    0.1 * data["Certifications"] +
    0.15 * data["Projects"] +
    0.1 * data["Hackathons"] +
    0.25 * data["Communication Score"]
)

placement_prob = (placement_score - placement_score.min()) / (placement_score.max() - placement_score.min())
placement_status = np.where(np.random.rand(n_samples) < placement_prob, "Placed", "Not Placed")

# Salary package only for placed students
salary = np.where(
    placement_status == "Placed",
    np.round(np.random.normal(4, 1.5, size=n_samples).clip(2, 12), 2),
    0.0
)

df_placement = pd.DataFrame(data)
df_placement["Placement Status"] = placement_status
df_placement["Salary (LPA)"] = salary

df_placement.head()

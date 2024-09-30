- 👋 Hi, I’m @sowmyamanthena1
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
sowmyamanthena1/sowmyamanthena1 is a ✨ special ✨ repository because its `R
import java.util.Scanner;

// Base class Insurance
class Insurance {
    private String insuranceNo;
    private String insuranceName;
    private double amountCovered;

    // Public properties
    public String getInsuranceNo() {
        return insuranceNo;
    }

    public void setInsuranceNo(String insuranceNo) {
        this.insuranceNo = insuranceNo;
    }

    public String getInsuranceName() {
        return insuranceName;
    }

    public void setInsuranceName(String insuranceName) {
        this.insuranceName = insuranceName;
    }

    public double getAmountCovered() {
        return amountCovered;
    }

    public void setAmountCovered(double amountCovered) {
        this.amountCovered = amountCovered;
    }
}

// Child class MotorInsurance
class MotorInsurance extends Insurance {
    private double idv; // Insured Declared Value
    private float depPercent; // Depreciation Percentage

    // Public properties
    public double getIdv() {
        return idv;
    }

    public void setIdv(double idv) {
        this.idv = idv;
    }

    public float getDepPercent() {
        return depPercent;
    }

    public void setDepPercent(float depPercent) {
        this.depPercent = depPercent;
    }

    // Calculate premium for motor insurance
    public double calculatePremium() {
        idv = getAmountCovered() - ((getAmountCovered() * depPercent) / 100);
        return (idv * 0.03); // 3% of IDV
    }
}

// Child class LifeInsurance
class LifeInsurance extends Insurance {
    private int policyTerm; // Policy term in years
    private float benefitPercent; // Benefit Percentage

    // Public properties
    public int getPolicyTerm() {
        return policyTerm;
    }

    public void setPolicyTerm(int policyTerm) {
        this.policyTerm = policyTerm;
    }

    public float getBenefitPercent() {
        return benefitPercent;
    }

    public void setBenefitPercent(float benefitPercent) {
        this.benefitPercent = benefitPercent;
    }

    // Calculate premium for life insurance
    public double calculatePremium() {
        return (getAmountCovered() - ((getAmountCovered() * benefitPercent) / 100)) / policyTerm;
    }
}

// Main class to drive the program
public class Program {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Input for Insurance details
        System.out.print("Insurance Number: ");
        String insuranceNo = scanner.nextLine();

        System.out.print("Insurance Name: ");
        String insuranceName = scanner.nextLine();

        System.out.print("Amount Covered: ");
        double amountCovered = scanner.nextDouble();

        System.out.println("Select:");
        System.out.println("1. Life Insurance");
        System.out.println("2. Motor Insurance");
        int option = scanner.nextInt();

        // Create appropriate insurance object
        if (option == 1) {
            LifeInsurance lifeInsurance = new LifeInsurance();
            lifeInsurance.setInsuranceNo(insuranceNo);
            lifeInsurance.setInsuranceName(insuranceName);
            lifeInsurance.setAmountCovered(amountCovered);

            // Additional inputs for Life Insurance
            System.out.print("Policy Term: ");
            int policyTerm = scanner.nextInt();
            lifeInsurance.setPolicyTerm(policyTerm);

            System.out.print("Benefit Percent: ");
            float benefitPercent = scanner.nextFloat();
            lifeInsurance.setBenefitPercent(benefitPercent);

            // Calculate premium and display
            double premium = addPolicy(lifeInsurance, option);
            System.out.println("Calculated Premium: " + premium);
        } else if (option == 2) {
            MotorInsurance motorInsurance = new MotorInsurance();
            motorInsurance.setInsuranceNo(insuranceNo);
            motorInsurance.setInsuranceName(insuranceName);
            motorInsurance.setAmountCovered(amountCovered);

            // Additional inputs for Motor Insurance
            System.out.print("Depreciation Percent: ");
            float depPercent = scanner.nextFloat();
            motorInsurance.setDepPercent(depPercent);

            // Calculate premium and display
            double premium = addPolicy(motorInsurance, option);
            System.out.println("Calculated Premium: " + premium);
        } else {
            System.out.println("Invalid option selected.");
        }
        
        scanner.close();
    }

    public static double addPolicy(Insurance ins, int opt) {
        if (opt == 1) {
            return ((LifeInsurance) ins).calculatePremium(); // Call calculatePremium for Life Insurance
        } else {
            return ((MotorInsurance) ins).calculatePremium(); // Call calculatePremium for Motor Insurance
        }
    }
}

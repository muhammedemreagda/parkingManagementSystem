import java.util.*;

class Vehicle {
    String licensePlate;
    String driverName;
    String department;

    public Vehicle(String licensePlate, String driverName, String department) {
        this.licensePlate = licensePlate;
        this.driverName = driverName;
        this.department = department;
    }
}

public class ParkingManagement {
    private static final int TOTAL_CAPACITY = 50;
    private int currentOccupancy = 0;
    private final Map<String, Vehicle> registeredVehicles = new HashMap<>();
    private final Set<String> reservedSpots = new HashSet<>();

    public void vehicleEntry(Scanner scanner) {
        if (currentOccupancy >= TOTAL_CAPACITY) {
            System.out.println("Error: Parking lot is full! Please try again later.");
            return;
        }

        System.out.print("Enter License Plate: ");
        String licensePlate = scanner.nextLine();

        if (registeredVehicles.containsKey(licensePlate)) {
            System.out.println("Error: Vehicle is already parked.");
            return;
        }

        System.out.print("Driver Name: ");
        String driverName = scanner.nextLine();
        System.out.print("Department: ");
        String department = scanner.nextLine();

        registeredVehicles.put(licensePlate, new Vehicle(licensePlate, driverName, department));
        currentOccupancy++;
        System.out.println("Vehicle successfully registered!");
    }

    public void vehicleExit(Scanner scanner) {
        System.out.print("Enter License Plate: ");
        String licensePlate = scanner.nextLine();

        if (!registeredVehicles.containsKey(licensePlate)) {
            System.out.println("Error: Vehicle not found in the parking lot.");
            return;
        }

        registeredVehicles.remove(licensePlate);
        currentOccupancy--;
        System.out.println("Vehicle successfully exited!");
    }

    public void reserveSpot(Scanner scanner) {
        System.out.print("Enter License Plate: ");
        String licensePlate = scanner.nextLine();

        if (reservedSpots.contains(licensePlate)) {
            System.out.println("Error: Spot already reserved.");
            return;
        }

        System.out.print("Enter the desired time slot (e.g., 12.00-12.30): ");
        String timeSlot = scanner.nextLine();
        reservedSpots.add(licensePlate);
        System.out.println("Reservation successfully completed!");
    }

    public void displayParkingStatus() {
        System.out.println("\nCurrent Parking Status:");
        System.out.println("Total Capacity: " + TOTAL_CAPACITY);
        System.out.println("Current Occupancy: " + currentOccupancy);
        System.out.println("Available Spots: " + (TOTAL_CAPACITY - currentOccupancy));
        registeredVehicles.values().forEach(vehicle -> 
            System.out.println("- License Plate: " + vehicle.licensePlate + ", Driver: " + vehicle.driverName + ", Department: " + vehicle.department));
    }

    public static void main(String[] args) {
        ParkingManagement pm = new ParkingManagement();
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\n1. Vehicle Entry\n2. Vehicle Exit\n3. Reserve a Spot\n4. Display Parking Status\n5. Exit");
            System.out.print("Choose an option: ");
            choice = scanner.nextInt();
            scanner.nextLine();

            switch (choice) {
                case 1 -> pm.vehicleEntry(scanner);
                case 2 -> pm.vehicleExit(scanner);
                case 3 -> pm.reserveSpot(scanner);
                case 4 -> pm.displayParkingStatus();
            }
        } while (choice != 5);
    }
}

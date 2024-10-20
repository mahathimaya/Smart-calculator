import java.io.*;
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class QuickLinkShortener {
    private static final String DATA_FILE = "urls.txt";
    private Map<String, String> urlMap = new HashMap<>();

    public QuickLinkShortener() {
        loadUrlMappings();
    }

    // Load existing mappings from the file
    private void loadUrlMappings() {
        try (BufferedReader reader = new BufferedReader(new FileReader(DATA_FILE))) {
            String line;
            while ((line = reader.readLine()) != null) {
                String[] parts = line.split(" ");
                if (parts.length == 2) {
                    urlMap.put(parts[0], parts[1]);
                }
            }
        } catch (IOException e) {
            System.out.println("Could not load URLs: " + e.getMessage());
        }
    }

    // Save mappings to the file
    private void saveUrlMappings() {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(DATA_FILE))) {
            for (var entry : urlMap.entrySet()) {
                writer.write(entry.getKey() + " " + entry.getValue());
                writer.newLine();
            }
        } catch (IOException e) {
            System.out.println("Could not save URLs: " + e.getMessage());
        }
    }

    // Shorten a URL and return the short link
    public String shortenUrl(String longUrl) {
        for (var entry : urlMap.entrySet()) {
            if (entry.getValue().equals(longUrl)) return entry.getKey();
        }
        String shortLink = String.valueOf(urlMap.size() + 1);
        urlMap.put(shortLink, longUrl);
        saveUrlMappings();
        return shortLink;
    }

    // Retrieve the original URL using the short link
    public String retrieveOriginalUrl(String shortLink) {
        return urlMap.get(shortLink);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        QuickLinkShortener shortener = new QuickLinkShortener();
        
        System.out.println("Welcome to QuickLink Shortener!");
        
        while (true) {
            System.out.print("Enter 'shorten', 'retrieve', or 'exit': ");
            String command = scanner.nextLine().toLowerCase();

            switch (command) {
                case "shorten":
                    System.out.pri

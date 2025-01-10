# Team_gusqls
연암공대 해커톤 고교생팀으로 참가한 gusqls팀입니다.

## 연암공대 해커톤 제출 코드

```C++
#include <iostream>
#include <fstream>
#include <string>

struct Location {
    double latitude;
    double longitude;
};

Location getUserLocationFromGPS() {
    std::ifstream gpsFile("gps_data.txt");
    Location userLocation;

    if (gpsFile.is_open()) {
        gpsFile >> userLocation.latitude >> userLocation.longitude;
        gpsFile.close();
    } else {
        std::cerr << "Error: Could not open GPS data file.\n";
        userLocation = {0.0, 0.0};
    }
    return userLocation;
}

int main() {
    Location userLocation = getUserLocationFromGPS();
    if (userLocation.latitude == 0.0 && userLocation.longitude == 0.0) {
        std::cout << "Unable to fetch GPS data.\n";
        return 1;
    }

    std::cout << "Your current location (from GPS): \n";
    std::cout << "Latitude: " << userLocation.latitude << "\n";
    std::cout << "Longitude: " << userLocation.longitude << "\n";
    
    return 0;
}
```


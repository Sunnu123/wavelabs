#include <iostream>
#include <vector>
#include <cmath>

using namespace std;

double calculateDistance(int x1, int y1, int x2, int y2) {
    return sqrt((x2 - x1) * (x2 - x1) + (y2 - y1) * (y2 - y1));
}

int calculateSignalQuality(int xi, int yi, int qi, int x, int y) {
    double distance = calculateDistance(xi, yi, x, y);
    return floor(qi / (1 + distance));
}

vector<int> findMaxNetworkQuality(vector<vector<int>>& towers, int radius) {
    int maxQuality = 0;
    vector<int> maxCoordinate = {0, 0};

    for (int x = 0; x <= 50; x++) {
        for (int y = 0; y <= 50; y++) {
            int networkQuality = 0;
            for (const auto& tower : towers) {
                int xi = tower[0];
                int yi = tower[1];
                int qi = tower[2];
                double distance = calculateDistance(xi, yi, x, y);
                if (distance <= radius) {
                    networkQuality += calculateSignalQuality(xi, yi, qi, x, y);
                }
            }
            if (networkQuality > maxQuality) {
                maxQuality = networkQuality;
                maxCoordinate = {x, y};
            }
            else if (networkQuality == maxQuality && x < maxCoordinate[0]) {
                maxCoordinate = {x, y};
            }
            else if (networkQuality == maxQuality && x == maxCoordinate[0] && y < maxCoordinate[1]) {
                maxCoordinate = {x, y};
            }
        }
    }

    return maxCoordinate;
}

int main() {
    vector<vector<int>> towers = {{1, 2, 5}, {2, 1, 7}, {3, 1, 9}};
    int radius = 2;

    vector<int> maxNetworkQuality = findMaxNetworkQuality(towers, radius);

    cout << "Max Network Quality Coordinate: [" << maxNetworkQuality[0] << ", " << maxNetworkQuality[1] << "]" << endl;

    return 0;
}

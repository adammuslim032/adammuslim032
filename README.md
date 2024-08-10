#include <iostream>
#include <chrono>
#include <thread>
#include <iomanip>

void displayCurrentTime() {
    using namespace std::chrono;
    while (true) {
        auto now = system_clock::now();
        auto now_c = system_clock::to_time_t(now);
        std::tm* now_tm = std::localtime(&now_c);

        std::cout << "\r" << std::put_time(now_tm, "%H:%M:%S") << std::flush;

        std::this_thread::sleep_for(seconds(1));
    }
}

int main() {
    std::cout << "Clock started. Press Ctrl+C to exit." << std::endl;
    displayCurrentTime();
    return 0;
}

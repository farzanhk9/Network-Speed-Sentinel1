# A professional tool to test and log internet speed (Download, Upload, and Ping).
import speedtest
import json

def run_speed_test():
    """Performs a real-time internet speed test."""
    print("⏳ Testing network speed, please wait...")
    st = speedtest.Speedtest()
    st.get_best_server()
    
    results = {
        "Download (Mbps)": round(st.download() / 1_000_000, 2),
        "Upload (Mbps)": round(st.upload() / 1_000_000, 2),
        "Ping (ms)": st.results.ping,
        "Server": st.results.server['name']
    }
    return results

if __name__ == "__main__":
    test_data = run_speed_test()
    print(json.dumps(test_data, indent=4))

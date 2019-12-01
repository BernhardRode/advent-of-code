fn fuel_weight(mass: i64) -> i64 {
    let t: f64 = mass as f64 / 3.0;
    return t.floor() as i64 - 2;
}

fn recursive_fuel_weight(mass: i64, weight: i64) -> i64 {
    let t: i64 = fuel_weight(mass);
    if t < 0 {
        return weight;
    } else {
        return recursive_fuel_weight(t, weight + t);
    }
}

fn calculate_mass_of_modules(arr: &[i64]) -> i64 {
    let mut sum: i64 = 0;
    for i in 0..arr.len() {
        let weight = recursive_fuel_weight(arr[i], 0);
        sum = sum + weight;
    }   
    return sum;
}

fn main() {
    let basea: i64 = 100756;
    let baseb: i64 = 1969;
    let day1 = fuel_weight(basea);
    let test1a = recursive_fuel_weight(basea, 0);
    let test1b = recursive_fuel_weight(baseb, 0);
    let test2a_inputs: [i64; 1] = [basea];
    let test2b_inputs: [i64; 1] = [baseb];
    let test2a = calculate_mass_of_modules(&test2a_inputs);
    let test2b = calculate_mass_of_modules(&test2b_inputs);
    
    let day2_inputs: [i64; 100] = [
        139301, 84565, 124180, 133902, 138726, 62665, 142967, 95598, 118044, 73234, 76476, 51634,
        71582, 63619, 148430, 134733, 101537, 101140, 144543, 102233, 62048, 128633, 130113, 92531,
        73820, 54964, 103485, 96364, 104119, 121954, 79215, 99235, 120179, 69237, 145584, 79193,
        50684, 146481, 67783, 112741, 85024, 62298, 54083, 137704, 116561, 76862, 81410, 96341,
        89992, 132926, 97955, 74751, 147553, 121496, 113303, 119671, 120871, 114278, 125628,
        144275, 78826, 87092, 65883, 87517, 93974, 55358, 100922, 113304, 115728, 144556, 91728,
        86367, 55283, 101841, 55454, 140703, 70706, 98173, 106920, 126984, 148960, 77909, 128304,
        140036, 81044, 141419, 126770, 52787, 115783, 128647, 125986, 124506, 113935, 142203,
        106404, 78433, 146573, 68575, 63563, 115616
    ];
    let step2 = calculate_mass_of_modules(&day2_inputs);
    println!("Step 1 - Solution {}", day1);
    println!("Step 2 - Test1a {}", test1a);
    println!("Step 2 - Test1b {}", test1b);
    println!("Step 2 - Test2a {}", test2a);
    println!("Step 2 - Test2b {}", test2b);
    println!("step 2 - Solution {}", step2);
}

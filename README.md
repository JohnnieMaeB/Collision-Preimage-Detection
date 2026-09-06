# Assignment 2: Hash Function Properties

Small Python scripts demonstrating three properties of cryptographic hash functions (SHA-256): collision resistance, preimage resistance, and the avalanche effect.

## Files

### `a2_collision.py`
`find_collision(n)` — demonstrates a **collision attack**. Repeatedly generates random 20-character strings, hashes each with SHA-256, and truncates the digest to its first `n` bytes. Stores each truncated hash in a dictionary; once two different strings produce the same truncated hash, returns them as a tuple `(string1, string2)`.

```python
from a2_collision import find_collision

s1, s2 = find_collision(2)  # find a collision on the first 2 bytes of SHA-256
```

### `a2_preimage.py`
`find_preimage(target, n)` — demonstrates a **preimage attack**. Given a `target` hash and a byte count `n`, repeatedly generates random 20-character strings and hashes them until one is found whose SHA-256 digest matches the first `n` bytes of `target`. Returns the matching string.

```python
from a2_preimage import find_preimage

match = find_preimage(target_hash, 2)  # find a string matching the first 2 bytes of target_hash
```

### `a2_hamming.py`
`hammingdistance(hex1, hex2)` — computes the **Hamming distance** (number of differing bits) between two hex-encoded values. Converts each to its binary representation and counts mismatched bits, padding for any length difference. Used to measure the avalanche effect (how much a hash output changes for a small change in input).

```python
from a2_hamming import hammingdistance

distance = hammingdistance(hex1, hex2)
```

## Requirements

Python 3, standard library only (`hashlib`, `string`, `random`).

## Notes

- `n` controls the number of leading bytes compared, which controls the difficulty of the collision/preimage search (smaller `n` = faster to find, since fewer bits must match).
- These scripts are for educational purposes, illustrating why hash truncation weakens both collision and preimage resistance.

# Code-Comic-2<img width="1080" height="2340" alt="1778" src="https://github.com/user-attachments/assets/60f576c0-5140-4f94-9d66-4b44aad9eee4" />
<img width="1080" height="2340" alt="1783" src="https://github.com/user-attachments/assets/4f89eb42-0479-4693-95ef-4f31ed4f6c3a" />
<img width="1080" height="2340" alt="1785" src="https://github.com/user-attachments/assets/693d2f98-8b50-471f-913e-ee99f23691f6" />
<img width="1344" height="2912" alt="1802" src="https://github.com/user-attachments/assets/c9357c42-48ab-4d6e-8cce-3fd79022e6b0" />
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract CodeComics {
    struct Character {
        string name;
        bytes32 encryptedDialogue;
        uint256 quantumKey;
    }

    Character[] public characters;
    mapping(uint256 => string) public scenes;

    constructor() {
        characters.push(Character({
            name: "GolfingBunny",
            encryptedDialogue: keccak256(abi.encodePacked("Why so serious? *swings quantum club*")),
            quantumKey: 0xBUNNY_2026
        }));

        characters.push(Character({
            name: "SkatingBoy",
            encryptedDialogue: keccak256(abi.encodePacked("Entropy is my ramp! *flips convex curve*")),
            quantumKey: 0xSK8R_2026
        }));

        characters.push(Character({
            name: "AbstractForce",
            encryptedDialogue: keccak256(abi.encodePacked("I am the gradient of chaos! *optimal transport engages*")),
            quantumKey: 0xFORCE_2026
        }));

        scenes[0] = "Scene 1: GolfingBunny hits a quantum ball, warping spacetime. SkatingBoy rides the entropy wave.";
        scenes[1] = "Scene 2: AbstractForce disrupts the gradient, but GolfingBunny calculates the optimal path.";
        scenes[2] = "Scene 3: SkatingBoy performs a convex flip, encrypting reality itself. *Post-quantum collision*";
    }

    function decryptDialogue(uint256 charIndex, uint256 key) public pure returns (string memory) {
        require(charIndex < characters.length, "Invalid character");
        if (key == characters[charIndex].quantumKey) {
            return string(abi.decode(characters[charIndex].encryptedDialogue, (bytes)));
        }
        return "Access denied: Post-quantum encryption active.";
    }

    function generateArtHash(uint256 sceneId) public view returns (bytes32) {
        return keccak256(abi.encodePacked(scenes[sceneId], block.timestamp));
    }
}

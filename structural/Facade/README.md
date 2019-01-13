# Facade

**Structural design pattern.**

The Facade Pattern provides a unified interface to a set of interfaces in as subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.

### Example

``` Java

class CPU {
    public void freeze() { ... }
    public void jump(long position) { ... }
    public void execute() { ... }
}

class HardDrive {
    public byte[] read(long lba, int size) { ... }
}

class Memory {
    public void load(long position, byte[] data) { ... }
}

/* Facade */

class ComputerFacade {
    private CPU processor;
    private Memory ram;
    private HardDrive hd;

    public ComputerFacade() {
        this.processor = new CPU();
        this.ram = new Memory();
        this.hd = new HardDrive();
    }

    public void start() {
        processor.freeze();
        ram.load(BOOT_ADDRESS, hd.read(BOOT_SECTOR, SECTOR_SIZE));
        processor.jump(BOOT_ADDRESS);
        processor.execute();
    }
}

/* Client */

class You {
    public static void main(String[] args) {
        ComputerFacade computer = new ComputerFacade();
        computer.start();
    }
}
```
### Documentation

https://www.youtube.com/watch?v=ANlcc2p9kCU

### Applicability

Use the Facade pattern when:

* you want to provide a simple interface to a complex subsystem. 

* there are many dependencies between clients and the implementation classes of an abstraction. Introduce a facade to decouple the subsystem from clients and other subsystems, thereby promoting subsystem independence and portability.

* you want to layer your subsystems. Use a facade to define an entry point to each subsystem level.

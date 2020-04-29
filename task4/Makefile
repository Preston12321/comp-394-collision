all: partials collision

.PHONY: partials
partials: collide.c
	gcc -o collide collide.c
	head -c 4224 collide > prefix.bin
	tail -c +4544 collide > suffix.bin
	(head -c 4416 collide | tail -c 64 -) > infix.bin
	md5collgen -p prefix.bin -o collision1.bin collision2.bin
	tail -c 128 collision1.bin > contents1.bin
	tail -c 128 collision2.bin > contents2.bin

.PHONY: collision
collision: prefix.bin contents1.bin infix.bin contents1.bin suffix.bin
	cat prefix.bin contents1.bin infix.bin contents1.bin suffix.bin > benign
	cat prefix.bin contents2.bin infix.bin contents1.bin suffix.bin > malicious
	sudo chmod +x benign malicious

.PHONY: sum
sum: benign malicious
	md5sum benign malicious

.PHONY: clean
clean:
	rm -f collide benign malicious *.bin

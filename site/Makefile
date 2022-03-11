generate:
	rm -rf public
	docker build --target generate -o public .

dev:
	rm -rf public
	docker build --target server -t resume-site-server .
	docker run --rm -v ${PWD}:/site -p 1313:1313 -it --name resume-site-server resume-site-server

# Show and Tell model using TensorFlow

## How to run it:

1) Install Bazel [link](https://docs.bazel.build/versions/master/install.html) It is a build system.

	Ensure you have the latest tensorflow and numpy libraries.

	Install [NLTK](http://www.nltk.org/install.html). Then, follow [this](http://www.nltk.org/data.html) to install the package 'punkt'

2) Download this repo as a .zip or clone it

3) Download any of the desired checkpoint files:

	[2M iterations finetuned checkpoint file](https://drive.google.com/open?id=1oWyegL4Z-rMlDGsYa3hIBma3tojdhZ9u)
	
	[1M iterations checkpoint file](https://drive.google.com/open?id=1lOf3kEzM4aI_a9NmogosID4WQMIOTdEp)
	
	Put the files inside the folder named 'model'

4) Install [Git](https://git-scm.com/) if you haven't already. Open the show-and-tell folder, and press right-click -> Git Bash here

	Now, in the opened command terminal, type the following:
	
	```
	
	# No spaces around the = sign, will cause trouble
	
	# Path to the model checkpoint
	# Note that you can also use model.ckpt-1000000
	CHECKPOINT_PATH=model/model.ckpt-2000000
	
	# Path to the vocabulary file
	VOCAB_PATH=model/word_counts.txt
	
	# Path to the image file you want to caption
	IMAGE_PATH=model/test_images/1.jpg

	# Build the inference binary, no need to run this while changing images
	bazel build -c opt im2txt/run_inference

	# Run inference to generate captions, this can take a while
	bazel-bin/im2txt/run_inference --checkpoint_path=${CHECKPOINT_PATH} --vocab_file=${VOCAB_PATH} --input_files=${IMAGE_PATH}
	
	```
	
	You should see the output in the bash window itself.

# GPT-AutoPilot

A ChatGPT API powered Python script that can create multi-file applications in any programming language (or any plaintext-based content for that matter). Just tell it what you want to build, and it will build it and ask you clarifying questions along the way.

GPT-AutoPilot uses an iterative process, so after it has accomplished the task, it will ask you if you need some modifications. You can also run the script with an existing project in the `code` folder and it will make modifications to it based on your prompt. **Note that the AI has the ability to delete and modify files, so have a backup**

# Usage

GPT-AutoPilot works on both Linux and Windows (and probably macOS) and it has [standalone packages](https://github.com/unconv/gpt-autopilot/releases/tag/v0.3.0), that don't need the Python interpreter.

## Linux

You can either clone the repository and run `gpt-autopilot.py` or you can [download](https://github.com/unconv/gpt-autopilot/releases/download/v0.3.0/gpt-autopilot-linux-ubuntu-0.3.0.zip) the standalone package.

1\. Export your [OpenAI API key](https://platform.openai.com/account/api-keys) as `OPENAI_API_KEY` environment variable or put it in the `config.json` file (see `config.sample.json`). You can also run the program directly, and it will ask you for your API key.

```console
$ export OPENAI_API_KEY=YOUR_API_KEY
```

2\. Install the **latest** version of the `openai` python package
```console
$ pip install --upgrade openai
```

3\. Run the script. It will ask you for a prompt.

```console
$ ./gpt-autopilot.py
```

4\. For example, tell it to "create a JavaScript inventory application for the browser with a form that can add products with a name, quantity and price. Save the products to localstorage and list them in a table in the application. Calculate the total price of the products in the inventory. Add CSS styles to make the application look professional. Add a Inventory System header and hide the product add form when the page is printed."

## Windows: Standalone Package

On Windows, you can [download](https://github.com/unconv/gpt-autopilot/releases/download/v0.3.0/gpt-autopilot-windows-0.3.0.zip) the standalone package, unzip it and run `gpt-autopilot.exe`. It will ask you for your API key.

## Windows: with Python interpreter

You can also [download](https://github.com/unconv/gpt-autopilot/archive/refs/heads/master.zip) or clone the repository and install it manually. You need [Python](https://www.python.org/) to be installed on your machine.

After you have downloaded and unzipped, or cloned the repository, go into the `gpt-autopilot` folder and do the following:

1\. Save your [OpenAI API key](https://platform.openai.com/account/api-keys) in the `OPENAI_API_KEY` environment variable or put it in the `config.json` file (see `config.sample.json`). You can also run the program directly, and it will ask you for your API key.

```console
> set OPENAI_API_KEY=YOUR_API_KEY
```

2\. Install the **latest** version of the `openai` python package
```console
> pip install --upgrade openai
```

3\. Run the script. It will ask you for a prompt.

```console
> python gpt-autopilot.py
```

## Where does the output go?

The files will be written to the `code` directory, relative to the path you ran the program from. If you use the `--versions` flag, the files will be written to the `versions` directory.

## Does it work with GPT-3.5?

The default model is `gpt-4-0613` and it works best, but you can still use the `gpt-3.5-turbo-16k-0613` or `gpt-3.5-turbo-0613` model. Just note that they are not as capable as GPT-4. To change, add `"model": "gpt-3.5-turbo-16k-0613"` to the `config.json` file. Make sure to use the 0613 model since only that supports function calling.

## Multi-version branching

With the new `--versions` flag you can create multiple versions of a project at the same time. This is recommended, as sometimes retrying a prompt will produce a better outcome.

For example, you can create 3 versions of the same project by running:

```console
$ ./gpt-autopilot --versions 3
```

After all the versions have been created, you can inspect them and GPT-AutoPilot will ask you, which one you want to iterate over. It will then create 3 more versions of that version with your next prompt and you can repeat this process until the project is ready.

All versions and version iterations are stored in separate folders in the `versions` folder.

## System Message

You can customize the system message by editing the `system_message` file. The system message will affect how the agent acts. For example, you can add a code style guide to it.

## Demo: GPT-4

https://github.com/unconv/gpt-autopilot/assets/120440395/78f0fb79-7f40-4aee-b6df-f9bea1457b5f

## Demo: GPT-3.5

https://github.com/unconv/gpt-autopilot/assets/120440395/34c814e9-9360-4c08-b776-98366ccc37b7

## Support

If you like this code, consider [buying me a coffee](https://buymeacoffee.com/unconv) and/or subscribing to my [YouTube-channel](https://youtube.com/@unconv)

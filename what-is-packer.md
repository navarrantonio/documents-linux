#### ¿What is Packer?
Packer is an open source tool for creating identical machine images for multiple platforms from a single source configuration. Packer is lightweight, runs on every major operating system, and is highly performant, creating machine images for multiple platforms in parallel. Packer does not replace configuration management like Chef or Puppet. In fact, when building images, Packer is able to use tools like Chef or Puppet to install software onto the image.

A machine image is a single static unit that contains a pre-configured operating system and installed software which is used to quickly create new running machines. Machine image formats change for each platform. Some examples include AMIs for EC2, VMDK/VMX files for VMware, OVF exports for VirtualBox, etc.

Packer works from templates. The templates are JSON files that tell Packer what kind of virtual machine you want to create, the steps to perform to install the operating system and the commands or scripts to be executed after installation.

Once we have created the template, Packer allows to automatically create as many virtual machines as we need. Logically, the more virtual machines we create from a template, the more profitable the time used in the development of the template, but even if we only create the virtual machine once, the template will serve as documentation and specification of the process.


#### Use Cases
By now you should know what Packer does and what the benefits of image creation are. In this section, we'll enumerate some of the use cases for Packer. Note that this is not an exhaustive list by any means. There are definitely use cases for Packer not listed here. This list is just meant to give you an idea of how Packer may improve your processes.

#### Continuous Delivery
Packer is lightweight, portable, and command-line driven. This makes it the perfect tool to put in the middle of your continuous delivery pipeline. Packer can be used to generate new machine images for multiple platforms on every change to Chef/Puppet.

As part of this pipeline, the newly created images can then be launched and tested, verifying the infrastructure changes work. If the tests pass, you can be confident that the image will work when deployed. This brings a new level of stability and testability to infrastructure changes.

#### Dev/Prod Parity
Packer helps keep development, staging, and production as similar as possible. Packer can be used to generate images for multiple platforms at the same time. So if you use AWS for production and VMware (perhaps with Vagrant) for development, you can generate both an AMI and a VMware machine using Packer at the same time from the same template.

Mix this in with the continuous delivery use case above, and you have a pretty slick system for consistent work environments from development all the way through to production.

#### Appliance/Demo Creation
Since Packer creates consistent images for multiple platforms in parallel, it is perfect for creating appliances and disposable product demos. As your software changes, you can automatically create appliances with the software pre-installed. Potential users can then get started with your software by deploying it to the environment of their choice.

Packaging up software with complex requirements has never been so easy. Or enjoyable, if you ask me.

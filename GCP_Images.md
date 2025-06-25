🖥️ GCP VM Image Listing & Popular Image Families
🔍 Image Listing Script
Run this script in Cloud Shell, Linux/macOS terminal, or Git Bash (Windows) to list common GCP image families:

bash
Copy
Edit
echo "🔍 Ubuntu Images:"
gcloud compute images list --project=ubuntu-os-cloud --filter="family:ubuntu*" --no-standard-images

echo "🔍 Debian Images:"
gcloud compute images list --project=debian-cloud --filter="family:debian*" --no-standard-images

echo "🔍 CentOS Images:"
gcloud compute images list --project=centos-cloud --filter="family:centos*" --no-standard-images

echo "🔍 Rocky Linux Images:"
gcloud compute images list --project=rocky-linux-cloud --no-standard-images

echo "🔍 RHEL Images:"
gcloud compute images list --project=rhel-cloud --no-standard-images

echo "🔍 SUSE Images:"
gcloud compute images list --project=suse-cloud --no-standard-images

echo "🔍 Windows Server Images:"
gcloud compute images list --project=windows-cloud --filter="name~'windows-server'" --no-standard-images
📊 Table of Popular Image Families
OS	Image Family	Image Project	Example Create Command
Ubuntu 22.04	ubuntu-2204-lts	ubuntu-os-cloud	--image-family=ubuntu-2204-lts --image-project=ubuntu-os-cloud
Ubuntu 20.04	ubuntu-2004-lts	ubuntu-os-cloud	--image-family=ubuntu-2004-lts --image-project=ubuntu-os-cloud
Debian 11	debian-11	debian-cloud	--image-family=debian-11 --image-project=debian-cloud
Debian 10	debian-10	debian-cloud	--image-family=debian-10 --image-project=debian-cloud
CentOS 7	centos-7	centos-cloud	--image-family=centos-7 --image-project=centos-cloud
Rocky Linux 9	rocky-linux-9	rocky-linux-cloud	--image-family=rocky-linux-9 --image-project=rocky-linux-cloud
RHEL 9	rhel-9	rhel-cloud	--image-family=rhel-9 --image-project=rhel-cloud
SUSE Linux	sles-15	suse-cloud	--image-family=sles-15 --image-project=suse-cloud
Windows 2022	windows-2022	windows-cloud	--image-family=windows-2022 --image-project=windows-cloud
Windows 2019	windows-2019	windows-cloud	--image-family=windows-2019 --image-project=windows-cloud


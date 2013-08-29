latest_tag=$(git tag -l *.*.* --contains $(git rev-list --tags --max-count=1))

if [[ ! "$latest_tag" =~ ^[0-9]+\.[0-9]+\.[0-9]+$ ]]; then
	echo "The \"latest\" tag did not exist, or did not point to a commit which also had a semantic version tag."
	exit 1
fi

major=$(echo "$latest_tag" | awk -F '.' '{print $1}')
minor=$(echo "$latest_tag" | awk -F '.' '{print $2}')
patch=$(echo "$latest_tag" | awk -F '.' '{print $3}')

echo "Latest semantic version tag: ${major}.${minor}.${patch}"

case "$1" in
	major)
		echo "Bumping major version."
		major=$(( $major + 1 ))
		minor=0
		patch=0
		;;
	minor)
		echo "Bumping minor version."
		minor=$(( $minor + 1 ))
		patch=0
		;;
	patch|*)
		echo "Bumping patch version."
		patch=$(( $patch + 1 ))
		;;
esac

echo "New semantic version is: ${major}.${minor}.${patch}"
echo -n "Do you want to tag the current commit with that version? [y/N]: "

read answer

if [[ "$answer" =~ (y|Y|yes) ]]; then
	version="${major}.${minor}.${patch}"
	tag_message="Version $version"
	latest_message_version="$version"

	[ $major -eq 0 ] && tag_message="$tag_message Beta"
	[ $major -eq 0 ] && latest_message_version="$latest_message_version Beta"

	# Add the tag
	git tag -a $version -m "$tag_message" > /dev/null
	git tag -af latest -m "Latest recommended version ($latest_message_version)" > /dev/null

	echo "Latest tags:"
	git tag -n1 | tail -n5
else
	echo "Aborted. No tags where added!"
fi

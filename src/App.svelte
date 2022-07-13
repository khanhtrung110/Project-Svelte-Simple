<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte"

    let title = "";
    let subtitle = "";
    let address = "";
    let email = "";
    let description = "";
    let imageUrl = "";

    let meetups = [
        {
            id: "m1",
            title: "Coding BootCamp",
            subtitle: "Learn to code in 2 hours",
            description: "In this meet up friend",
            imageUrl:
                "https://ecdn.game4v.com/g4v-content/uploads/2021/11/15163810/game4v-naruto-minato-con-song-1-1636969089-59.jpg",
            address: "27th New York",
            contactEmail: "code@test.com",
        },
        {
            id: "m2",
            title: "Swim Together",
            subtitle: "Let' go for some swiming",
            description: "We will simply swin some rounds!",
            imageUrl:
                "https://thuvienanime.com/wp-content/uploads/2022/03/dac-diem-cua-Sasuke.jpg",
            address: "27th New York",
            contactEmail: "swim@test.com",
        },
    ];

    function addMeetup() {
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            subtitle: subtitle,
            description: description,
            imageUrl: imageUrl,
            contactEmail: email,
            address: address,
        };

        meetups = [newMeetup, ...meetups];
    }
</script>

<Header />
<main>
    <form on:submit|preventDefault={addMeetup}>
        <TextInput
            id="title"
            label="Title"
            value={title}
            on:input={(event) => (title = event.target.value)}
        />
        <TextInput
            id="subtitle"
            label="Subtitle"
            value={subtitle}
            on:input={(event) => (subtitle = event.target.value)}
        />
        <TextInput
            id="address"
            label="Address"
            value={address}
            on:input={(event) => (address = event.target.value)}
        />
        <TextInput
            id="imageUrl"
            label="Image URL"
            value={imageUrl}
            on:input={(event) => (imageUrl = event.target.value)}
        />
        <TextInput
            id="email"
            label="Email"
            value={email}
            on:input={(event) => (email = event.target.value)}
        />
        <TextInput
            id="description"
            label="Description"
            value={description}
            on:input={(event) => (description = event.target.value)}
        />
        <Button type="submit" caption="Save" />
    </form>
    <MeetupGrid {meetups} />
</main>

<style>
    main {
        margin-top: 5rem;
    }
    form{
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>

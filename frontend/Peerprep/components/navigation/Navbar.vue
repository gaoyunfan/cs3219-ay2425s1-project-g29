<script setup>
import { signOut } from 'firebase/auth';

const auth = useFirebaseAuth();
const user = useCurrentUser();

console.log("user", user)
import NavLink from '~/components/navigation/NavLink.vue';
function handleSignOut() {
    signOut(auth)
}
</script>


<template>
    <nav class="bg-muted/70 shadow-sm border-b border-border">
        <div class="w-full mx-auto flex items-center justify-between py-2 px-3">
            <div class="flex items-center space-x-8">
                <img src="@/assets/PeerPrep.png" alt="Logo" class="w-[52px]" />
                <div class="flex items-center space-x-6">
                    <NavLink to="/" exact>Home</NavLink>
                    <NavLink to="/questions">Questions</NavLink>
                </div>
            </div>

            <DropdownMenu>
                <DropdownMenuTrigger as-child>
                    <Avatar size="xs"
                        class="hover:shadow-xl hover:bg-gray-300  transition-all duration-300 cursor-pointer">
                        <AvatarImage :src="user.photoURL" alt="User Avatar" />
                        <AvatarFallback>CN</AvatarFallback>
                    </Avatar>

                </DropdownMenuTrigger>
                <DropdownMenuContent class="w-fit" align="end">
                    <DropdownMenuItem>
                        <NuxtLink to="/users/settings">Settings</NuxtLink>
                    </DropdownMenuItem>
                    <DropdownMenuItem @click="handleSignOut">Sign out</DropdownMenuItem>
                </DropdownMenuContent>
            </DropdownMenu>
        </div>
    </nav>
</template>

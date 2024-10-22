<script setup>
import bonus from "@/assets/img/balance/bonus.png";
import mintwin from "@/assets/img/balance/mintwin.png";
import usd from "@/assets/img/currency/usd.svg";
import fs from "@/assets/img/fs.png";
import fb from "@/assets/img/fb.png";
import fg from "@/assets/img/fg.png";
import { ref } from "vue";

const activeButton = ref(0);
const isEmpty = ref(false);
const list = [
    {
        slug: "main",
        title: "Основной баланс",
        buttons: [
            {
                cur: "USD",
                value: "$1 283.93208",
                icon: usd,
                footer: null,
            },
            {
                cur: "MintWin",
                value: "213.43 USD",
                icon: mintwin,
                footer: null,
            },
        ],
    },
    {
        slug: "bonus",
        title: "Бонусный баланс",
        buttons: [
            {
                cur: "Bonus",
                value: "213.43 USD",
                icon: bonus,
                footer: null,
            },
        ],
    },
    {
        slug: "game",
        title: "Бонусные игры",
        buttons: [
            {
                cur: "FreeGame",
                value: "213.43 USD",
                icon: fg,
                footer: {
                    left: "1 день 01:23:46",
                    right: "10 шт",
                },
            },
            {
                cur: "FreeBet",
                value: "213.43 USD",
                icon: fb,
                footer: {
                    left: "2 дня 02:55:27",
                    right: "10 шт",
                },
            },
            {
                cur: "FreeSpin",
                value: "213.43 USD",
                icon: fs,
                footer: {
                    left: "3 дня 10:36:12",
                    right: "10 шт",
                },
            },
        ],
    },
];
</script>

<template>
    <div class="animate__animated animate__fadeIn flex w-[317px] flex-col gap-2 divide-y-2 divide-[#1E2023] rounded-[15px] bg-[#161719] p-[15px] sm:w-[325px]">
        <div @click="isEmpty = !isEmpty" v-for="item in list" class="flex flex-col gap-[5px] pb-[14px] pt-[14px] first:pt-0 last:pb-0">
            <h3 class="text-sm font-normal leading-[150%] text-[#949494] [font-family:Stapel]">{{ item.title }}</h3>

            <template v-if="!isEmpty || item.slug !== 'game'">
                <ul class="flex w-full flex-col gap-1.5">
                    <li class="w-full" v-for="(button, i) in item.buttons" :key="i">
                        <button
                            @click="activeButton = i"
                            class="flex w-full flex-col items-center justify-center overflow-hidden rounded-[10px] border-[1px] border-[#242527] bg-[#1D1E20] px-[15px] transition-colors duration-300"
                            :class="[button.footer !== null ? 'h-[78px]' : 'h-[50px]']"
                        >
                            <div class="flex w-full items-center justify-between">
                                <div class="flex items-center gap-2">
                                    <img class="w-[30px]" :src="button.icon" :alt="button.cur" />
                                    <span class="text-[14px] uppercase text-[#D4D4D4] sm:text-[16px]">{{ button.cur }}</span>
                                </div>

                                <span class="text-base font-normal text-[#AFB0B2]">{{ button.value }}</span>
                            </div>

                            <template v-if="button.footer">
                                <div class="my-1 h-px w-full shrink-0 rounded-md [background:#242527]"></div>

                                <div
                                    class="flex w-full items-center justify-between text-center text-[13px] font-bold leading-5 text-[#424242] [font-family:Stapel]"
                                >
                                    <div>{{ button.footer.left }}</div>
                                    <div>{{ button.footer.right }}</div>
                                </div>
                            </template>
                        </button>
                    </li>
                </ul>
            </template>

            <template v-else>
                <div class="flex h-[50px] w-full shrink-0 items-center justify-center rounded-[10px] border border-solid border-[#242527] [background:#1D1E20]">
                    <p class="text-center text-[13px] font-bold leading-[normal] tracking-[0.39px] text-[#696A6C] [font-family:Stapel]">
                        Нет активных предложений
                    </p>
                </div>

                <button
                    class="flex h-[35px] w-full items-center justify-center gap-2.5 rounded-lg px-[76px] pb-4 pt-[19px] text-center text-sm font-bold uppercase leading-5 text-[#101010] [background:#84FD4B] [font-family:Stapel]"
                >
                    Получить
                </button>
            </template>
        </div>
    </div>
</template>

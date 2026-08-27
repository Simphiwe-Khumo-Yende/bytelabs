<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from '@/components/ui/card'
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs'
import { Badge } from '@/components/ui/badge'
import { Button } from '@/components/ui/button'
import { Avatar, AvatarFallback, AvatarImage } from '@/components/ui/avatar'
import { Tooltip, TooltipContent, TooltipProvider, TooltipTrigger } from '@/components/ui/tooltip'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from '@/components/ui/accordion'
import { Alert, AlertDescription, AlertTitle } from '@/components/ui/alert'
import { Switch } from '@/components/ui/switch'
import { Progress } from '@/components/ui/progress'
import {
  Dialog, DialogContent, DialogDescription, DialogFooter,
  DialogHeader, DialogTitle, DialogTrigger,
} from '@/components/ui/dialog'
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select'
import { Checkbox } from '@/components/ui/checkbox'
import { RadioGroup, RadioGroupItem } from '@/components/ui/radio-group'
import { Slider } from '@/components/ui/slider'
import { Textarea } from '@/components/ui/textarea'
import { Skeleton } from '@/components/ui/skeleton'
import { Popover, PopoverContent, PopoverTrigger } from '@/components/ui/popover'
import { ToggleGroup, ToggleGroupItem } from '@/components/ui/toggle-group'
import { HoverCard, HoverCardContent, HoverCardTrigger } from '@/components/ui/hover-card'
import { Separator } from '@/components/ui/separator'

const pageRef = ref(null)
const redesignProgress = ref(8)
const mobileAppProgress = ref(8)
const budgetValue = ref([65])

onMounted(() => {
  setTimeout(() => {
    redesignProgress.value = 82
    mobileAppProgress.value = 46
  }, 500)

  if (!pageRef.value) return
  inView(
    pageRef.value,
    () => {
      animate(
        pageRef.value.querySelectorAll('[data-s]'),
        { opacity: [0, 1], y: [24, 0] },
        { duration: 0.5, delay: stagger(0.06), easing: [0.25, 0.1, 0.25, 1] }
      )
    },
    { amount: 0.05 }
  )
})
</script>

<template>
  <div ref="pageRef" class="ui-showcase-page">
    <section class="bg-background pt-28 pb-16 px-6 text-center">
      <Badge variant="outline" class="uppercase tracking-widest text-[11px] mb-5">UI/UX Design</Badge>
      <h1 class="text-5xl font-semibold tracking-tight mb-4">From inspiration to creation</h1>
      <p class="text-muted-foreground max-w-lg mx-auto text-base leading-relaxed">
        A living product built from shadcn-vue — every panel below is a real, interactive component.
      </p>
    </section>

    <section class="bg-white py-16 px-6">
      <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-6 gap-5">

        <!-- Tabs hero tile with floating Button + Badge chips -->
        <div data-s class="lg:col-span-4 relative" style="opacity:0">
          <Tabs default-value="account">
            <TabsList class="grid w-full max-w-sm grid-cols-2">
              <TabsTrigger value="account">Account</TabsTrigger>
              <TabsTrigger value="password">Password</TabsTrigger>
            </TabsList>
            <TabsContent value="account">
              <Card class="shadow-sm">
                <CardHeader>
                  <CardTitle>Account</CardTitle>
                  <CardDescription>Make changes to your account here. Click save when you're done.</CardDescription>
                </CardHeader>
                <CardContent class="space-y-2">
                  <div class="space-y-1">
                    <Label for="name">Name</Label>
                    <Input id="name" default-value="Pedro Duarte" />
                  </div>
                  <div class="space-y-1">
                    <Label for="username">Username</Label>
                    <Input id="username" default-value="@peduarte" />
                  </div>
                </CardContent>
                <CardFooter>
                  <Button>Save changes</Button>
                </CardFooter>
              </Card>
            </TabsContent>
            <TabsContent value="password">
              <Card class="shadow-sm">
                <CardHeader>
                  <CardTitle>Password</CardTitle>
                  <CardDescription>Change your password here. After saving, you'll be logged out.</CardDescription>
                </CardHeader>
                <CardContent class="space-y-2">
                  <div class="space-y-1">
                    <Label for="current">Current password</Label>
                    <Input id="current" type="password" />
                  </div>
                  <div class="space-y-1">
                    <Label for="new">New password</Label>
                    <Input id="new" type="password" />
                  </div>
                </CardContent>
                <CardFooter>
                  <Button>Save password</Button>
                </CardFooter>
              </Card>
            </TabsContent>
          </Tabs>

          <!-- Floating chips, absolute on desktop -->
          <div class="mt-5 flex flex-wrap gap-3 lg:absolute lg:-top-6 lg:-right-6 lg:mt-0 lg:z-10 lg:flex-col lg:w-44">
            <Card class="shadow-lg rotate-[-2deg] hover:rotate-0 transition-transform">
              <CardContent class="flex flex-wrap gap-2 py-3">
                <Button size="sm">Button</Button>
                <Button size="sm" variant="secondary">Secondary</Button>
                <Button size="sm" variant="outline">Outline</Button>
              </CardContent>
            </Card>
            <Card class="shadow-lg rotate-[2deg] hover:rotate-0 transition-transform">
              <CardContent class="flex flex-wrap gap-2 py-3">
                <Badge>Badge</Badge>
                <Badge variant="secondary">Secondary</Badge>
              </CardContent>
            </Card>
          </div>
        </div>

        <!-- Team / Avatar + Tooltip -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>4 people are shaping this project</CardTitle>
              <CardDescription>Design, engineering, and product working in sync.</CardDescription>
            </CardHeader>
            <CardContent>
              <TooltipProvider>
                <div class="flex -space-x-2">
                  <Tooltip>
                    <TooltipTrigger as-child>
                      <Avatar class="ring-2 ring-background">
                        <AvatarImage src="https://github.com/shadcn.png" alt="@shadcn" />
                        <AvatarFallback>CN</AvatarFallback>
                      </Avatar>
                    </TooltipTrigger>
                    <TooltipContent><p>@shadcn &mdash; Design</p></TooltipContent>
                  </Tooltip>
                  <Tooltip>
                    <TooltipTrigger as-child>
                      <Avatar class="ring-2 ring-background">
                        <AvatarImage src="https://github.com/leerob.png" alt="@leerob" />
                        <AvatarFallback>LR</AvatarFallback>
                      </Avatar>
                    </TooltipTrigger>
                    <TooltipContent><p>@leerob &mdash; Engineering</p></TooltipContent>
                  </Tooltip>
                  <Tooltip>
                    <TooltipTrigger as-child>
                      <Avatar class="ring-2 ring-background">
                        <AvatarImage src="https://github.com/evilrabbit.png" alt="@evilrabbit" />
                        <AvatarFallback>ER</AvatarFallback>
                      </Avatar>
                    </TooltipTrigger>
                    <TooltipContent><p>@evilrabbit &mdash; Product</p></TooltipContent>
                  </Tooltip>
                  <Tooltip>
                    <TooltipTrigger as-child>
                      <Avatar class="ring-2 ring-background">
                        <AvatarFallback>+1</AvatarFallback>
                      </Avatar>
                    </TooltipTrigger>
                    <TooltipContent><p>You</p></TooltipContent>
                  </Tooltip>
                </div>
              </TooltipProvider>
            </CardContent>
          </Card>
        </div>

        <!-- Notifications card -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Notifications</CardTitle>
              <CardDescription>You have 3 unread messages.</CardDescription>
            </CardHeader>
            <CardContent>
              <p class="text-sm text-muted-foreground">Your subscription renews in 3 days.</p>
            </CardContent>
            <CardFooter class="flex gap-2">
              <Button class="flex-1">Check it out</Button>
              <Button variant="outline" class="flex-1">Dismiss</Button>
            </CardFooter>
          </Card>
        </div>

        <!-- Delivery Progress card -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Delivery Progress</CardTitle>
              <CardDescription>How close each engagement is to launch.</CardDescription>
            </CardHeader>
            <CardContent class="space-y-4">
              <div class="space-y-1.5">
                <div class="flex justify-between text-sm">
                  <span>Website Redesign</span>
                  <span class="text-muted-foreground">{{ redesignProgress }}%</span>
                </div>
                <Progress :model-value="redesignProgress" />
              </div>
              <div class="space-y-1.5">
                <div class="flex justify-between text-sm">
                  <span>Mobile App</span>
                  <span class="text-muted-foreground">{{ mobileAppProgress }}%</span>
                </div>
                <Progress :model-value="mobileAppProgress" />
              </div>
            </CardContent>
          </Card>
        </div>

        <!-- Accordion FAQ -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Frequently asked</CardTitle>
              <CardDescription>Answers pulled straight from the component docs.</CardDescription>
            </CardHeader>
            <CardContent>
              <Accordion type="single" collapsible class="w-full">
                <AccordionItem value="item-1">
                  <AccordionTrigger>Is it accessible?</AccordionTrigger>
                  <AccordionContent>Yes. It adheres to the WAI-ARIA design pattern.</AccordionContent>
                </AccordionItem>
                <AccordionItem value="item-2">
                  <AccordionTrigger>Is it styled?</AccordionTrigger>
                  <AccordionContent>Yes. It comes with default styles that match the other components.</AccordionContent>
                </AccordionItem>
                <AccordionItem value="item-3">
                  <AccordionTrigger>Is it animated?</AccordionTrigger>
                  <AccordionContent>Yes. It's animated by default, but you can disable it if you prefer.</AccordionContent>
                </AccordionItem>
              </Accordion>
            </CardContent>
          </Card>
        </div>

        <!-- Preferences / Switch -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Preferences</CardTitle>
              <CardDescription>Control how we keep you in the loop.</CardDescription>
            </CardHeader>
            <CardContent class="space-y-4">
              <div class="flex items-center justify-between">
                <Label for="email-notifs">Email notifications</Label>
                <Switch id="email-notifs" default-checked />
              </div>
              <div class="flex items-center justify-between">
                <Label for="marketing-emails">Marketing emails</Label>
                <Switch id="marketing-emails" />
              </div>
              <div class="flex items-center justify-between">
                <Label for="airplane-mode">Airplane mode</Label>
                <Switch id="airplane-mode" />
              </div>
            </CardContent>
          </Card>
        </div>

        <!-- Alert -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <Alert class="h-full">
            <AlertTitle>Heads up!</AlertTitle>
            <AlertDescription>You can add components to your app using the CLI.</AlertDescription>
          </Alert>
        </div>

        <!-- Dialog -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Team member details</CardTitle>
              <CardDescription>Update profile info and save changes.</CardDescription>
            </CardHeader>
            <CardContent>
              <Dialog>
                <DialogTrigger as-child>
                  <Button variant="outline">Edit Profile</Button>
                </DialogTrigger>
                <DialogContent class="sm:max-w-[425px]">
                  <DialogHeader>
                    <DialogTitle>Edit profile</DialogTitle>
                    <DialogDescription>Make changes to your profile here. Click save when you're done.</DialogDescription>
                  </DialogHeader>
                  <div class="grid gap-4 py-4">
                    <div class="space-y-1">
                      <Label for="dialog-name">Name</Label>
                      <Input id="dialog-name" default-value="Pedro Duarte" />
                    </div>
                    <div class="space-y-1">
                      <Label for="dialog-username">Username</Label>
                      <Input id="dialog-username" default-value="@peduarte" />
                    </div>
                  </div>
                  <DialogFooter>
                    <Button type="submit">Save changes</Button>
                  </DialogFooter>
                </DialogContent>
              </Dialog>
            </CardContent>
          </Card>
        </div>

        <!-- Select (dark) -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <div class="dark bg-background rounded-2xl p-5 h-full">
            <Card class="shadow-sm h-full border-none">
              <CardHeader>
                <CardTitle>Pick a service</CardTitle>
                <CardDescription>What are we building together?</CardDescription>
              </CardHeader>
              <CardContent>
                <Select default-value="web">
                  <SelectTrigger class="w-full">
                    <SelectValue placeholder="Select a service" />
                  </SelectTrigger>
                  <SelectContent>
                    <SelectItem value="web">Web Development</SelectItem>
                    <SelectItem value="mobile">Mobile Apps</SelectItem>
                    <SelectItem value="design">UI/UX Design</SelectItem>
                    <SelectItem value="backend">Backend Systems</SelectItem>
                  </SelectContent>
                </Select>
              </CardContent>
            </Card>
          </div>
        </div>

        <!-- Checkbox -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Project checklist</CardTitle>
              <CardDescription>What's already locked in.</CardDescription>
            </CardHeader>
            <CardContent class="space-y-3">
              <div class="flex items-center gap-2">
                <Checkbox id="brief" default-checked />
                <Label for="brief">Brief received</Label>
              </div>
              <div class="flex items-center gap-2">
                <Checkbox id="wireframes" default-checked />
                <Label for="wireframes">Wireframes approved</Label>
              </div>
              <div class="flex items-center gap-2">
                <Checkbox id="handoff" />
                <Label for="handoff">Dev handoff</Label>
              </div>
            </CardContent>
          </Card>
        </div>

        <!-- Radio Group (dark) -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <div class="dark bg-background rounded-2xl p-5 h-full">
            <Card class="shadow-sm h-full border-none">
              <CardHeader>
                <CardTitle>Choose a plan</CardTitle>
                <CardDescription>Pricing that scales with scope.</CardDescription>
              </CardHeader>
              <CardContent>
                <RadioGroup default-value="growth" class="space-y-2">
                  <div class="flex items-center gap-2">
                    <RadioGroupItem id="starter" value="starter" />
                    <Label for="starter">Starter</Label>
                  </div>
                  <div class="flex items-center gap-2">
                    <RadioGroupItem id="growth" value="growth" />
                    <Label for="growth">Growth</Label>
                  </div>
                  <div class="flex items-center gap-2">
                    <RadioGroupItem id="scale" value="scale" />
                    <Label for="scale">Scale</Label>
                  </div>
                </RadioGroup>
              </CardContent>
            </Card>
          </div>
        </div>

        <!-- Slider -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Monthly budget</CardTitle>
              <CardDescription>Drag to estimate your engagement size.</CardDescription>
            </CardHeader>
            <CardContent class="space-y-3">
              <Slider v-model="budgetValue" :max="100" :step="1" />
              <p class="text-sm text-muted-foreground">${{ budgetValue[0] * 100 }} / month</p>
            </CardContent>
          </Card>
        </div>

        <!-- Textarea (dark) -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <div class="dark bg-background rounded-2xl p-5 h-full">
            <Card class="shadow-sm h-full border-none">
              <CardHeader>
                <CardTitle>Project brief</CardTitle>
                <CardDescription>Tell us what you're building.</CardDescription>
              </CardHeader>
              <CardContent>
                <Textarea placeholder="We're looking to redesign our onboarding flow..." />
              </CardContent>
            </Card>
          </div>
        </div>

        <!-- Skeleton -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Loading state</CardTitle>
              <CardDescription>What users see while data streams in.</CardDescription>
            </CardHeader>
            <CardContent class="flex items-center gap-3">
              <Skeleton class="h-12 w-12 rounded-full" />
              <div class="space-y-2">
                <Skeleton class="h-4 w-[160px]" />
                <Skeleton class="h-4 w-[120px]" />
              </div>
            </CardContent>
          </Card>
        </div>

        <!-- Popover (dark) -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <div class="dark bg-background rounded-2xl p-5 h-full">
            <Card class="shadow-sm h-full border-none">
              <CardHeader>
                <CardTitle>Quick estimate</CardTitle>
                <CardDescription>Peek at a rough timeline.</CardDescription>
              </CardHeader>
              <CardContent>
                <Popover>
                  <PopoverTrigger as-child>
                    <Button variant="outline">Open estimate</Button>
                  </PopoverTrigger>
                  <PopoverContent class="w-72">
                    <p class="text-sm font-medium mb-1">Typical timeline</p>
                    <p class="text-sm text-muted-foreground">Most engagements ship in 4&ndash;6 weeks from kickoff to launch.</p>
                  </PopoverContent>
                </Popover>
              </CardContent>
            </Card>
          </div>
        </div>

        <!-- Toggle Group -->
        <div data-s class="lg:col-span-2" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>View mode</CardTitle>
              <CardDescription>Switch how the portfolio is displayed.</CardDescription>
            </CardHeader>
            <CardContent>
              <ToggleGroup type="single" default-value="grid" variant="outline">
                <ToggleGroupItem value="list">List</ToggleGroupItem>
                <ToggleGroupItem value="grid">Grid</ToggleGroupItem>
                <ToggleGroupItem value="board">Board</ToggleGroupItem>
              </ToggleGroup>
            </CardContent>
          </Card>
        </div>

        <!-- Hover Card (dark) -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <div class="dark bg-background rounded-2xl p-5 h-full">
            <Card class="shadow-sm h-full border-none">
              <CardHeader>
                <CardTitle>Meet the team</CardTitle>
                <CardDescription>Hover a name for a quick preview.</CardDescription>
              </CardHeader>
              <CardContent>
                <HoverCard>
                  <HoverCardTrigger as-child>
                    <Button variant="link" class="px-0">@shadcn</Button>
                  </HoverCardTrigger>
                  <HoverCardContent class="w-72">
                    <div class="flex gap-3">
                      <Avatar>
                        <AvatarImage src="https://github.com/shadcn.png" alt="@shadcn" />
                        <AvatarFallback>CN</AvatarFallback>
                      </Avatar>
                      <div class="space-y-1">
                        <p class="text-sm font-semibold">@shadcn</p>
                        <p class="text-sm text-muted-foreground">Lead designer, obsessed with detail and dark mode.</p>
                      </div>
                    </div>
                  </HoverCardContent>
                </HoverCard>
              </CardContent>
            </Card>
          </div>
        </div>

        <!-- Separator -->
        <div data-s class="lg:col-span-3" style="opacity:0">
          <Card class="shadow-sm h-full">
            <CardHeader>
              <CardTitle>Explore more</CardTitle>
              <CardDescription>Jump straight to what you need.</CardDescription>
            </CardHeader>
            <CardContent>
              <div class="flex h-5 items-center gap-4 text-sm text-muted-foreground">
                <span>Blog</span>
                <Separator orientation="vertical" />
                <span>Docs</span>
                <Separator orientation="vertical" />
                <span>Source</span>
              </div>
            </CardContent>
          </Card>
        </div>

      </div>
    </section>

    <!-- Back-to-work CTA -->
    <section class="bg-background py-20 px-6 text-center">
      <router-link to="/#services" class="inline-flex items-center justify-center px-7 py-3 rounded-full bg-foreground text-background text-sm font-medium hover:opacity-85 transition-opacity">
        See what else we build
      </router-link>
    </section>
  </div>
</template>

<style scoped>
.ui-showcase-page {
  padding-top: 96px;
}
</style>


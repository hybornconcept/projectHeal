<script lang="ts">
  import ChevronLeft from "lucide-svelte/icons/chevron-left";
  import ChevronRight from "lucide-svelte/icons/chevron-right";
  import Copy from "lucide-svelte/icons/copy";
  import CreditCard from "lucide-svelte/icons/credit-card";
  import File from "lucide-svelte/icons/file";
  import House from "lucide-svelte/icons/house";
  import ChartLine from "lucide-svelte/icons/chart-line";
  import ListFilter from "lucide-svelte/icons/list-filter";
  import EllipsisVertical from "lucide-svelte/icons/ellipsis-vertical";
  import Package from "lucide-svelte/icons/package";
  import Package2 from "lucide-svelte/icons/package-2";
  import PanelLeft from "lucide-svelte/icons/panel-left";
  import Search from "lucide-svelte/icons/search";
  import Settings from "lucide-svelte/icons/settings";
  import ShoppingCart from "lucide-svelte/icons/shopping-cart";
  import Truck from "lucide-svelte/icons/truck";
  import UsersRound from "lucide-svelte/icons/users-round";

  import { Badge } from "$lib/components/ui/badge/index.js";

  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import * as DropdownMenu from "$lib/components/ui/dropdown-menu/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import * as Pagination from "$lib/components/ui/pagination/index.js";
  import { Progress } from "$lib/components/ui/progress/index.js";
  import { Separator } from "$lib/components/ui/separator/index.js";
  import * as Sheet from "$lib/components/ui/sheet/index.js";
  import * as Table from "$lib/components/ui/table/index.js";
  import * as Tabs from "$lib/components/ui/tabs/index.js";
  import * as Tooltip from "$lib/components/ui/tooltip/index.js";
</script>

<Tooltip.Provider>
  <div class="bg-muted/40 flex min-h-screen w-full flex-col">
    <aside class="bg-background fixed inset-y-0 left-0 z-10 hidden w-14 flex-col border-r sm:flex">
      <nav class="flex flex-col items-center gap-4 px-2 sm:py-5">
        <a
          href="##"
          class="bg-primary text-primary-foreground group flex h-9 w-9 shrink-0 items-center justify-center gap-2 rounded-full text-lg font-semibold md:h-8 md:w-8 md:text-base"
        >
          <Package2 class="h-4 w-4 transition-all group-hover:scale-110" />
          <span class="sr-only">Acme Inc</span>
        </a>
        <Tooltip.Root>
          <Tooltip.Trigger class="text-muted-foreground hover:text-foreground flex h-9 w-9 items-center justify-center rounded-lg transition-colors md:h-8 md:w-8">
            <House class="h-5 w-5" />
            <span class="sr-only">Dashboard</span>
          </Tooltip.Trigger>
          <Tooltip.Content side="right">Dashboard</Tooltip.Content>
        </Tooltip.Root>
        <Tooltip.Root>
          <Tooltip.Trigger class="text-muted-foreground hover:text-foreground flex h-9 w-9 items-center justify-center rounded-lg transition-colors md:h-8 md:w-8">
            <ShoppingCart class="h-5 w-5" />
            <span class="sr-only">Orders</span>
          </Tooltip.Trigger>
          <Tooltip.Content side="right">Orders</Tooltip.Content>
        </Tooltip.Root>
        <Tooltip.Root>
          <Tooltip.Trigger class="text-muted-foreground hover:text-foreground flex h-9 w-9 items-center justify-center rounded-lg transition-colors md:h-8 md:w-8">
            <Package class="h-5 w-5" />
            <span class="sr-only">Products</span>
          </Tooltip.Trigger>
          <Tooltip.Content side="right">Products</Tooltip.Content>
        </Tooltip.Root>
        <Tooltip.Root>
          <Tooltip.Trigger class="text-muted-foreground hover:text-foreground flex h-9 w-9 items-center justify-center rounded-lg transition-colors md:h-8 md:w-8">
            <UsersRound class="h-5 w-5" />
            <span class="sr-only">Customers</span>
          </Tooltip.Trigger>
          <Tooltip.Content side="right">Customers</Tooltip.Content>
        </Tooltip.Root>
        <Tooltip.Root>
          <Tooltip.Trigger class="text-muted-foreground hover:text-foreground flex h-9 w-9 items-center justify-center rounded-lg transition-colors md:h-8 md:w-8">
            <ChartLine class="h-5 w-5" />
            <span class="sr-only">Analytics</span>
          </Tooltip.Trigger>
          <Tooltip.Content side="right">Analytics</Tooltip.Content>
        </Tooltip.Root>
      </nav>
      <nav class="mt-auto flex flex-col items-center gap-4 px-2 sm:py-5">
        <Tooltip.Root>
          <Tooltip.Trigger class="text-muted-foreground hover:text-foreground flex h-9 w-9 items-center justify-center rounded-lg transition-colors md:h-8 md:w-8">
            <Settings class="h-5 w-5" />
            <span class="sr-only">Settings</span>
          </Tooltip.Trigger>
          <Tooltip.Content side="right">Settings</Tooltip.Content>
        </Tooltip.Root>
      </nav>
    </aside>
    <div class="flex flex-col sm:gap-4 sm:py-4 sm:pl-14">
      <header
        class="bg-background sticky top-0 z-30 flex h-14 items-center gap-4 border-b px-4 sm:static sm:h-auto sm:border-0 sm:bg-transparent sm:px-6"
      >
        <Sheet.Root>
          <Sheet.Trigger class="sm:hidden">
            <Button size="icon" variant="outline">
              <PanelLeft class="h-5 w-5" />
              <span class="sr-only">Toggle Menu</span>
            </Button>
          </Sheet.Trigger>
          <Sheet.Content side="left" class="sm:max-w-xs">
            <nav class="grid gap-6 text-lg font-medium">
              <a
                href="##"
                class="bg-primary text-primary-foreground group flex h-10 w-10 shrink-0 items-center justify-center gap-2 rounded-full text-lg font-semibold md:text-base"
              >
                <Package2 class="h-5 w-5 transition-all group-hover:scale-110" />
                <span class="sr-only">Acme Inc</span>
              </a>
              <a
                href="##"
                class="text-muted-foreground hover:text-foreground flex items-center gap-4 px-2.5"
              >
                <House class="h-5 w-5" />
                Dashboard
              </a>
              <a href="##" class="text-foreground flex items-center gap-4 px-2.5">
                <ShoppingCart class="h-5 w-5" />
                Orders
              </a>
              <a
                href="##"
                class="text-muted-foreground hover:text-foreground flex items-center gap-4 px-2.5"
              >
                <Package class="h-5 w-5" />
                Products
              </a>
              <a
                href="##"
                class="text-muted-foreground hover:text-foreground flex items-center gap-4 px-2.5"
              >
                <UsersRound class="h-5 w-5" />
                Customers
              </a>
              <a
                href="##"
                class="text-muted-foreground hover:text-foreground flex items-center gap-4 px-2.5"
              >
                <ChartLine class="h-5 w-5" />
                Settings
              </a>
            </nav>
          </Sheet.Content>
        </Sheet.Root>
 
        <div class="relative ml-auto flex-1 md:grow-0">
          <Search class="text-muted-foreground absolute left-2.5 top-2.5 h-4 w-4" />
          <Input
            type="search"
            placeholder="Search..."
            class="bg-background w-full rounded-lg pl-8 md:w-[200px] lg:w-[336px]"
          />
        </div>
        <DropdownMenu.Root>
          <DropdownMenu.Trigger>
            <Button 
              variant="outline"
              size="icon"
              class="overflow-hidden rounded-full"
            >
              <img
                src="/images/placeholder-user.jpg"
                width={36}
                height={36}
                alt="Avatar"
                class="overflow-hidden rounded-full"
              />
            </Button>
          </DropdownMenu.Trigger>
          <DropdownMenu.Content align="end">
            <DropdownMenu.Label>My Account</DropdownMenu.Label>
            <DropdownMenu.Separator />
            <DropdownMenu.Item>Settings</DropdownMenu.Item>
            <DropdownMenu.Item>Support</DropdownMenu.Item>
            <DropdownMenu.Separator />
            <DropdownMenu.Item>Logout</DropdownMenu.Item>
          </DropdownMenu.Content>
        </DropdownMenu.Root>
      </header>
      <main
        class="grid flex-1 items-start gap-4 p-4 sm:px-6 sm:py-0 md:gap-8 lg:grid-cols-3 xl:grid-cols-3"
      >
        <div class="grid auto-rows-max items-start gap-4 md:gap-8 lg:col-span-2">
          <div class="grid gap-4 sm:grid-cols-2 md:grid-cols-4 lg:grid-cols-2 xl:grid-cols-4">
            <Card.Root class="sm:col-span-2">
              <Card.Header class="pb-3">
                <Card.Title>Your Orders</Card.Title>
                <Card.Description class="max-w-lg text-balance leading-relaxed">
                  Introducing Our Dynamic Orders Dashboard for Seamless Management and
                  Insightful Analysis.
                </Card.Description>
              </Card.Header>
              <Card.Footer>
                <Button>Create New Order</Button>
              </Card.Footer>
            </Card.Root>
            <Card.Root>
              <Card.Header class="pb-2">
                <Card.Description>This Week</Card.Description>
                <Card.Title class="text-4xl">1329</Card.Title>
              </Card.Header>
              <Card.Content>
                <div class="text-muted-foreground text-xs">+25% from last week</div>
              </Card.Content>
              <Card.Footer>
                <Progress value={25} aria-label="25% increase" />
              </Card.Footer>
            </Card.Root>
            <Card.Root>
              <Card.Header class="pb-2">
                <Card.Description>This Month</Card.Description>
                <Card.Title class="text-3xl">5,329</Card.Title>
              </Card.Header>
              <Card.Content>
                <div class="text-muted-foreground text-xs">+10% from last month</div>
              </Card.Content>
              <Card.Footer>
                <Progress value={12} aria-label="12% increase" />
              </Card.Footer>
            </Card.Root>
          </div>
          <Tabs.Root value="week">
            <div class="flex items-center">
              <Tabs.List>
                <Tabs.Trigger value="week">Week</Tabs.Trigger>
                <Tabs.Trigger value="month">Month</Tabs.Trigger>
                <Tabs.Trigger value="year">Year</Tabs.Trigger>
              </Tabs.List>
              <div class="ml-auto flex items-center gap-2">
                <DropdownMenu.Root>
                  <DropdownMenu.Trigger>
                    <Button
                      variant="outline"
                      size="sm"
                      class="h-7 gap-1 text-sm"
                    >
                      <ListFilter class="h-3.5 w-3.5" />
                      <span class="sr-only sm:not-sr-only">Filter</span>
                    </Button>
                  </DropdownMenu.Trigger>
                  <DropdownMenu.Content align="end">
                    <DropdownMenu.Label>Filter by</DropdownMenu.Label>
                    <DropdownMenu.Separator />
                    <DropdownMenu.CheckboxItem checked>
                      Fulfilled
                    </DropdownMenu.CheckboxItem>
                    <DropdownMenu.CheckboxItem>Declined</DropdownMenu.CheckboxItem>
                    <DropdownMenu.CheckboxItem>Refunded</DropdownMenu.CheckboxItem>
                  </DropdownMenu.Content>
                </DropdownMenu.Root>
                <Button size="sm" variant="outline" class="h-7 gap-1 text-sm">
                  <File class="h-3.5 w-3.5" />
                  <span class="sr-only sm:not-sr-only">Export</span>
                </Button>
              </div>
            </div>
            <Tabs.Content value="week">
              <Card.Root>
                <Card.Header class="px-7">
                  <Card.Title>Orders</Card.Title>
                  <Card.Description>Recent orders from your store.</Card.Description>
                </Card.Header>
                <Card.Content>
                  <Table.Root class="w-full">
                    <Table.Header>
                      <Table.Row>
                        <Table.Head class="font-medium">Patient</Table.Head>
                        <Table.Head class="font-medium">Date</Table.Head>
                        <Table.Head class="font-medium">Status</Table.Head>
                        <Table.Head class="font-medium">Doctor</Table.Head>
                        <Table.Head class="font-medium">Actions</Table.Head>
                      </Table.Row>
                    </Table.Header>
                    <Table.Body>
                      <Table.Row class="border-b">
                        <Table.Cell class="py-4">
                          <div class="flex items-center gap-3">
                            <div class="flex h-8 w-8 items-center justify-center rounded-full bg-green-100 text-green-700">
                              PB
                            </div>
                            <div class="font-medium">Phoenix Baker</div>
                          </div>
                        </Table.Cell>
                        <Table.Cell class="text-muted-foreground">Jan 4, 2022</Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-1">
                            <div class="h-2 w-2 rounded-full bg-green-500"></div>
                            <span class="text-green-600">Scheduled</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-3">
                            <div class="h-8 w-8 overflow-hidden rounded-full bg-gray-100">
                              <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="Dr. Alex Ramirez" />
                            </div>
                            <span>Dr. Alex Ramirez</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex gap-2">
                            <Button variant="outline" size="sm" class="text-green-600 border-green-200 hover:bg-green-50 hover:border-green-300">Schedule</Button>
                            <Button variant="outline" size="sm" class="text-gray-500 border-gray-200 hover:bg-gray-50">Cancel</Button>
                          </div>
                        </Table.Cell>
                      </Table.Row>
                      <Table.Row class="border-b">
                        <Table.Cell class="py-4">
                          <div class="flex items-center gap-3">
                            <div class="flex h-8 w-8 items-center justify-center rounded-full bg-blue-100 text-blue-700">
                              CW
                            </div>
                            <div class="font-medium">Candice Wu</div>
                          </div>
                        </Table.Cell>
                        <Table.Cell class="text-muted-foreground">Jan 2, 2022</Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-1">
                            <div class="h-2 w-2 rounded-full bg-blue-500"></div>
                            <span class="text-blue-600">Pending</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-3">
                            <div class="h-8 w-8 overflow-hidden rounded-full bg-gray-100">
                              <img src="https://randomuser.me/api/portraits/men/45.jpg" alt="Dr. Michael May" />
                            </div>
                            <span>Dr. Michael May</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex gap-2">
                            <Button variant="outline" size="sm" class="text-green-600 border-green-200 hover:bg-green-50 hover:border-green-300">Schedule</Button>
                            <Button variant="outline" size="sm" class="text-gray-500 border-gray-200 hover:bg-gray-50">Cancel</Button>
                          </div>
                        </Table.Cell>
                      </Table.Row>
                      <Table.Row class="border-b">
                        <Table.Cell class="py-4">
                          <div class="flex items-center gap-3">
                            <div class="flex h-8 w-8 items-center justify-center rounded-full bg-blue-100 text-blue-700">
                              LS
                            </div>
                            <div class="font-medium">Lana Steiner</div>
                          </div>
                        </Table.Cell>
                        <Table.Cell class="text-muted-foreground">Jan 4, 2022</Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-1">
                            <div class="h-2 w-2 rounded-full bg-red-500"></div>
                            <span class="text-red-600">Cancelled</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-3">
                            <div class="h-8 w-8 overflow-hidden rounded-full bg-gray-100">
                              <img src="https://randomuser.me/api/portraits/women/68.jpg" alt="Dr. Jasmine Lee" />
                            </div>
                            <span>Dr. Jasmine Lee</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex gap-2">
                            <Button variant="outline" size="sm" class="text-green-600 border-green-200 hover:bg-green-50 hover:border-green-300">Schedule</Button>
                            <Button variant="outline" size="sm" class="text-gray-500 border-gray-200 hover:bg-gray-50">Cancel</Button>
                          </div>
                        </Table.Cell>
                      </Table.Row>
                      <Table.Row class="border-b">
                        <Table.Cell class="py-4">
                          <div class="flex items-center gap-3">
                            <div class="flex h-8 w-8 items-center justify-center rounded-full bg-orange-100 text-orange-700">
                              DC
                            </div>
                            <div class="font-medium">Drew Cano</div>
                          </div>
                        </Table.Cell>
                        <Table.Cell class="text-muted-foreground">Jan 8, 2022</Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-1">
                            <div class="h-2 w-2 rounded-full bg-green-500"></div>
                            <span class="text-green-600">Scheduled</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-3">
                            <div class="h-8 w-8 overflow-hidden rounded-full bg-gray-100">
                              <img src="https://randomuser.me/api/portraits/men/75.jpg" alt="Dr. Hardik Sharma" />
                            </div>
                            <span>Dr. Hardik Sharma</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex gap-2">
                            <Button variant="outline" size="sm" class="text-green-600 border-green-200 hover:bg-green-50 hover:border-green-300">Schedule</Button>
                            <Button variant="outline" size="sm" class="text-gray-500 border-gray-200 hover:bg-gray-50">Cancel</Button>
                          </div>
                        </Table.Cell>
                      </Table.Row>
                      <Table.Row class="border-b">
                        <Table.Cell class="py-4">
                          <div class="flex items-center gap-3">
                            <div class="flex h-8 w-8 items-center justify-center rounded-full bg-purple-100 text-purple-700">
                              NC
                            </div>
                            <div class="font-medium">Natali Craig</div>
                          </div>
                        </Table.Cell>
                        <Table.Cell class="text-muted-foreground">Jan 6, 2022</Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-1">
                            <div class="h-2 w-2 rounded-full bg-blue-500"></div>
                            <span class="text-blue-600">Pending</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex items-center gap-3">
                            <div class="h-8 w-8 overflow-hidden rounded-full bg-gray-100">
                              <img src="https://randomuser.me/api/portraits/women/45.jpg" alt="Dr. Aiyana Cruz" />
                            </div>
                            <span>Dr. Aiyana Cruz</span>
                          </div>
                        </Table.Cell>
                        <Table.Cell>
                          <div class="flex gap-2">
                            <Button variant="outline" size="sm" class="text-green-600 border-green-200 hover:bg-green-50 hover:border-green-300">Schedule</Button>
                            <Button variant="outline" size="sm" class="text-gray-500 border-gray-200 hover:bg-gray-50">Cancel</Button>
                          </div>
                        </Table.Cell>
                      </Table.Row>
                    </Table.Body>
                  </Table.Root>
                </Card.Content>
              </Card.Root>
            </Tabs.Content>
          </Tabs.Root>
        </div>
        <div>
          <Card.Root class="overflow-hidden">
            <Card.Header class="bg-muted/50 flex flex-row items-start">
              <div class="grid gap-0.5">
                <Card.Title class="group flex items-center gap-2 text-lg">
                  Order Oe31b70H
                  <Button
                    size="icon"
                    variant="outline"
                    class="h-6 w-6 opacity-0 transition-opacity group-hover:opacity-100"
                  >
                    <Copy class="h-3 w-3" />
                    <span class="sr-only">Copy Order ID</span>
                  </Button>
                </Card.Title>
                <Card.Description>Date: November 23, 2023</Card.Description>
              </div>
              <div class="ml-auto flex items-center gap-1">
                <Button size="sm" variant="outline" class="h-8 gap-1">
                  <Truck class="h-3.5 w-3.5" />
                  <span class="lg:sr-only xl:not-sr-only xl:whitespace-nowrap">
                    Track Order
                  </span>
                </Button>
                <DropdownMenu.Root>
                  <DropdownMenu.Trigger 
                    size="icon"
                    variant="outline"
                    class="h-8 w-8"
                  >
                    <EllipsisVertical class="h-3.5 w-3.5" />
                    <span class="sr-only">More</span>
                  </DropdownMenu.Trigger>
                  <DropdownMenu.Content align="end">
                    <DropdownMenu.Item>Edit</DropdownMenu.Item>
                    <DropdownMenu.Item>Export</DropdownMenu.Item>
                    <DropdownMenu.Separator />
                    <DropdownMenu.Item>Trash</DropdownMenu.Item>
                  </DropdownMenu.Content>
                </DropdownMenu.Root>
              </div>
            </Card.Header>
            <Card.Content class="p-6 text-sm">
              <div class="grid gap-3">
                <div class="font-semibold">Order Details</div>
                <ul class="grid gap-3">
                  <li class="flex items-center justify-between">
                    <span class="text-muted-foreground">
                      Glimmer Lamps x <span>2</span>
                    </span>
                    <span>250.00</span>
                  </li>
                  <li class="flex items-center justify-between">
                    <span class="text-muted-foreground">
                      Aqua Filters x <span>1</span>
                    </span>
                    <span>49.00</span>
                  </li>
                </ul>
                <Separator class="my-2" />
                <ul class="grid gap-3">
                  <li class="flex items-center justify-between">
                    <span class="text-muted-foreground">Subtotal</span>
                    <span>299.00</span>
                  </li>
                  <li class="flex items-center justify-between">
                    <span class="text-muted-foreground">Shipping</span>
                    <span>5.00</span>
                  </li>
                  <li class="flex items-center justify-between">
                    <span class="text-muted-foreground">Tax</span>
                    <span>25.00</span>
                  </li>
                  <li class="flex items-center justify-between font-semibold">
                    <span class="text-muted-foreground">Total</span>
                    <span>329.00</span>
                  </li>
                </ul>
              </div>
              <Separator class="my-4" />
              <div class="grid grid-cols-2 gap-4">
                <div class="grid gap-3">
                  <div class="font-semibold">Shipping Information</div>
                  <address class="text-muted-foreground grid gap-0.5 not-italic">
                    <span>Liam Johnson</span>
                    <span>1234 Main St.</span>
                    <span>Anytown, CA 12345</span>
                  </address>
                </div>
                <div class="grid auto-rows-max gap-3">
                  <div class="font-semibold">Billing Information</div>
                  <div class="text-muted-foreground">Same as shipping address</div>
                </div>
              </div>
              <Separator class="my-4" />
              <div class="grid gap-3">
                <div class="font-semibold">Customer Information</div>
                <dl class="grid gap-3">
                  <div class="flex items-center justify-between">
                    <dt class="text-muted-foreground">Customer</dt>
                    <dd>Liam Johnson</dd>
                  </div>
                  <div class="flex items-center justify-between">
                    <dt class="text-muted-foreground">Email</dt>
                    <dd>
                      <a href="mailto:">liam@acme.com</a>
                    </dd>
                  </div>
                  <div class="flex items-center justify-between">
                    <dt class="text-muted-foreground">Phone</dt>
                    <dd>
                      <a href="tel:">+1 234 567 890</a>
                    </dd>
                  </div>
                </dl>
              </div>
              <Separator class="my-4" />
              <div class="grid gap-3">
                <div class="font-semibold">Payment Information</div>
                <dl class="grid gap-3">
                  <div class="flex items-center justify-between">
                    <dt class="text-muted-foreground flex items-center gap-1">
                      <CreditCard class="h-4 w-4" />
                      Visa
                    </dt>
                    <dd>**** **** **** 4532</dd>
                  </div>
                </dl>
              </div>
            </Card.Content>
            <Card.Footer class="bg-muted/50 flex flex-row items-center border-t px-6 py-3">
              <div class="text-muted-foreground text-xs">
                Updated <time dateTime="2023-11-23">November 23, 2023</time>
              </div>
              <Pagination.Root count={10} class="ml-auto mr-0 w-auto">
                <Pagination.Content>
                  <Pagination.Item>
                    <Button size="icon" variant="outline" class="h-6 w-6">
                      <ChevronLeft class="h-3.5 w-3.5" />
                      <span class="sr-only">Previous Order</span>
                    </Button>
                  </Pagination.Item>
                  <Pagination.Item>
                    <Button size="icon" variant="outline" class="h-6 w-6">
                      <ChevronRight class="h-3.5 w-3.5" />
                      <span class="sr-only">Next Order</span>
                    </Button>
                  </Pagination.Item>
                </Pagination.Content>
              </Pagination.Root>
            </Card.Footer>
          </Card.Root>
        </div>
      </main>
    </div>
  </div>
</Tooltip.Provider>

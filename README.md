# Line Chart Using Recharts and Tailwind CSS

```tsx
import React from "react"
import {
  CartesianGrid,
  Legend,
  Line,
  LineChart,
  ResponsiveContainer,
  Tooltip,
  XAxis,
  YAxis,
} from "recharts"

import { numberWithCommas } from "@/lib/helper"
import { cn } from "@/lib/utils"

const data = [
  {
    name: "January",
    followers: 100,
    likes: 2110,
  },
  {
    name: "February",
    followers: 157,
    likes: 4532,
  },
  {
    name: "March",
    followers: 250,
    likes: 8953,
  },
  {
    name: "April",
    followers: 3400,
    likes: 14500,
  },
  {
    name: "May",
    followers: 8000,
    likes: 28043,
  },
  {
    name: "June",
    followers: 12605,
    likes: 50234,
  },
  {
    name: "July",
    followers: 23500,
    likes: 102340,
  },
]

export default function LineChartBefore() {
  return (
    <ResponsiveContainer width="100%" height="100%">
      <LineChart width={500} height={300} data={data}>
        <CartesianGrid strokeDasharray="3 3" opacity={0.3} vertical={false} />
        <XAxis
          dataKey="name"
          axisLine={false}
          tickLine={false}
          textAnchor="end"
          stroke="#e5e5e5"
          fontSize={14}
          interval={0}
        />
        <YAxis
          axisLine={false}
          tickLine={false}
          stroke="#e5e5e5"
          fontSize={14}
        />
        <Tooltip
          position={{ y: 0 }}
          wrapperStyle={{ outline: "none" }}
          cursor={{ fill: "#fafafa", opacity: "0.15" }}
          content={({ payload, label }) => {
            return (
              <div className="min-w-[8rem] divide-y divide-brand-200 rounded-md border border-brand-200 bg-brand-50 text-brand-700 shadow dark:divide-brand-700 dark:border-brand-700 dark:bg-brand-900 dark:text-brand-200">
                <p className="px-4 py-1.5">{label}</p>
                <div>
                  <ul className="px-4 py-1.5">
                    {payload.map((p, i) => {
                      return (
                        <li key={i} className="text-sm">
                          <svg
                            className={cn("mr-2 inline h-2 w-2")}
                            fill={i === 0 ? "#60a5fa" : "#f472b6"}
                            viewBox="0 0 8 8"
                          >
                            <circle cx={4} cy={4} r={4} />
                          </svg>
                          {numberWithCommas(p.value.toString())}
                        </li>
                      )
                    })}
                  </ul>
                </div>
              </div>
            )
          }}
        />
        <Legend
          layout="horizontal"
          verticalAlign="top"
          align="center"
          content={({ payload }) => {
            return (
              <ul className="flex w-fit gap-4 pb-6 pl-1">
                {payload.map((p, i) => (
                  <li key={i}>
                    <svg
                      className={cn("mr-2 inline h-2 w-2")}
                      fill={i === 0 ? "#60a5fa" : "#f472b6"}
                      viewBox="0 0 8 8"
                    >
                      <circle cx={4} cy={4} r={4} />
                    </svg>
                    {p.value}
                  </li>
                ))}
              </ul>
            )
          }}
        />
        <Line
          dataKey="followers"
          stroke="#60a5fa"
          dot={false}
          activeDot={{
            stroke: "#171717",
          }}
        />
        <Line
          dataKey="likes"
          stroke="#f472b6"
          dot={false}
          activeDot={{
            stroke: "#171717",
          }}
        />
      </LineChart>
    </ResponsiveContainer>
  )
}
```

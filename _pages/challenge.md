---
layout: page
permalink: /challenge/
title: Challenge
nav: true
nav_order: 3
---

This is an archive of my **30-Day Research & Practice Challenge**. 
I am building my expertise in Databases, NLP, and related application practice, one day at a time.

<br>

### 🗓️ Challenge Calendar
<style>
.challenge-calendar {
    margin-top: 15px;
    margin-bottom: 30px;
    padding: 16px;
    border: 1px solid var(--global-divider-color, #dee2e6);
    border-radius: 14px;
    background: var(--global-bg-color, #fff);
}

.challenge-calendar__toolbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 14px;
}

.challenge-calendar__title {
    font-size: 1.05rem;
    font-weight: 700;
    margin: 0;
}

.challenge-calendar__nav {
    display: flex;
    gap: 8px;
}

.challenge-calendar__button {
    border: 1px solid var(--global-divider-color, #dee2e6);
    background: transparent;
    border-radius: 999px;
    padding: 6px 12px;
    color: var(--global-text-color);
    cursor: pointer;
}

.challenge-calendar__button:hover {
    background: var(--global-bg-color, #f8f9fa);
}

.challenge-calendar__weekdays,
.challenge-calendar__grid {
    display: grid;
    grid-template-columns: repeat(7, minmax(0, 1fr));
    gap: 8px;
}

.challenge-calendar__weekday {
    text-align: center;
    font-size: 0.8rem;
    color: var(--global-text-color-light, #6c757d);
    padding-bottom: 4px;
}

.challenge-calendar__day,
.challenge-calendar__empty {
    min-height: 92px;
    border-radius: 12px;
}

.challenge-calendar__day {
    border: 1px solid var(--global-divider-color, #dee2e6);
    padding: 10px;
    background: linear-gradient(180deg, rgba(255,255,255,0.96), rgba(248,249,250,0.96));
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.challenge-calendar__day.is-current {
    border-color: #8da2ff;
    box-shadow: 0 0 0 1px rgba(141, 162, 255, 0.2) inset;
}

.challenge-calendar__day.is-empty {
    background: transparent;
    border: 1px dashed transparent;
}

.challenge-calendar__day.is-active {
    background: linear-gradient(135deg, #ffe8cc 0%, #d0ebff 50%, #d3f9d8 100%);
}

.challenge-calendar__date {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 8px;
    font-weight: 700;
}

html[data-theme="dark"] .challenge-calendar__date {
    color: #000;
}

.challenge-calendar__count {
    min-width: 22px;
    height: 22px;
    border-radius: 999px;
    background: var(--global-bg-color, #f1f3f5);
    display: inline-flex;
    align-items: center;
    justify-content: center;
    font-size: 0.75rem;
}

.challenge-calendar__dots {
    display: flex;
    flex-wrap: wrap;
    gap: 4px;
}

.challenge-calendar__dot {
    width: 8px;
    height: 8px;
    border-radius: 999px;
}

.challenge-calendar__dot.is-db { background: #ffa94d; }
.challenge-calendar__dot.is-nlp { background: #74c0fc; }
.challenge-calendar__dot.is-cloud { background: #8ce99a; }

.challenge-calendar__list {
    margin-top: 8px;
    display: flex;
    flex-wrap: wrap;
    gap: 4px;
    font-size: 0.82rem;
    line-height: 1.35;
}

.challenge-calendar__list a {
    display: inline-block;
    max-width: 100%;
    padding: 2px 6px;
    border-radius: 999px;
    background: rgba(255, 255, 255, 0.65);
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    text-decoration: none;
}

.challenge-calendar__more {
    display: inline-block;
    padding: 2px 6px;
    border-radius: 999px;
    background: rgba(0, 0, 0, 0.06);
    color: var(--global-text-color-light, #6c757d);
    white-space: nowrap;
}

@media (max-width: 768px) {
    .challenge-calendar__day,
    .challenge-calendar__empty {
        min-height: 76px;
    }

    .challenge-calendar__toolbar {
        flex-direction: column;
        align-items: flex-start;
    }
}
</style>

{% assign all_challenge_posts = site.challenge_db | concat: site.challenge_nlp | concat: site.challenge_cloud | sort: "date" | reverse %}
<div class="challenge-calendar" id="challenge-calendar">
    <div class="challenge-calendar__toolbar">
        <p class="challenge-calendar__title" data-calendar-label>Challenge Calendar</p>
        <div class="challenge-calendar__nav">
            <button class="challenge-calendar__button" type="button" data-calendar-prev>Previous</button>
            <button class="challenge-calendar__button" type="button" data-calendar-next>Next</button>
        </div>
    </div>

    <div class="challenge-calendar__weekdays">
        <div class="challenge-calendar__weekday">Sun</div>
        <div class="challenge-calendar__weekday">Mon</div>
        <div class="challenge-calendar__weekday">Tue</div>
        <div class="challenge-calendar__weekday">Wed</div>
        <div class="challenge-calendar__weekday">Thu</div>
        <div class="challenge-calendar__weekday">Fri</div>
        <div class="challenge-calendar__weekday">Sat</div>
    </div>

    <div class="challenge-calendar__grid" data-calendar-grid></div>
</div>

<script>
    window.challengePosts = [
        {% for post in all_challenge_posts %}
        {
            title: {{ post.title | jsonify }},
            url: {{ post.url | relative_url | jsonify }},
            date: {{ post.date | date: "%Y-%m-%d" | jsonify }},
            category: {{ post.collection | jsonify }},
            categoryLabel: {% if post.collection == "challenge_db" %}{{ "DB" | jsonify }}{% elsif post.collection == "challenge_nlp" %}{{ "NLP" | jsonify }}{% elsif post.collection == "challenge_cloud" %}{{ "Practice" | jsonify }}{% else %}{{ post.collection | jsonify }}{% endif %}
        }{% unless forloop.last %},{% endunless %}
        {% endfor %}
    ];
</script>

<script>
    (function () {
        const root = document.getElementById('challenge-calendar');
        if (!root) return;

        const posts = window.challengePosts || [];
        const grid = root.querySelector('[data-calendar-grid]');
        const label = root.querySelector('[data-calendar-label]');
        const prevButton = root.querySelector('[data-calendar-prev]');
        const nextButton = root.querySelector('[data-calendar-next]');
        const weekdayCount = 7;
        const categoryClass = {
            challenge_db: 'is-db',
            challenge_nlp: 'is-nlp',
            challenge_cloud: 'is-cloud'
        };

        function toDateKey(date) {
            const year = date.getFullYear();
            const month = String(date.getMonth() + 1).padStart(2, '0');
            const day = String(date.getDate()).padStart(2, '0');
            return `${year}-${month}-${day}`;
        }

        const postMap = posts.reduce((map, post) => {
            if (!map[post.date]) map[post.date] = [];
            map[post.date].push(post);
            return map;
        }, {});

        let activeMonth = new Date();
        if (posts.length > 0) {
            const latestPost = new Date(posts[0].date + 'T00:00:00');
            activeMonth = new Date(latestPost.getFullYear(), latestPost.getMonth(), 1);
        } else {
            activeMonth = new Date(activeMonth.getFullYear(), activeMonth.getMonth(), 1);
        }

        function renderCalendar() {
            const year = activeMonth.getFullYear();
            const month = activeMonth.getMonth();
            const firstDay = new Date(year, month, 1);
            const lastDay = new Date(year, month + 1, 0);
            const startOffset = firstDay.getDay();
            const totalDays = lastDay.getDate();
            const todayKey = toDateKey(new Date());

            label.textContent = firstDay.toLocaleDateString('en', { month: 'long', year: 'numeric' });
            grid.innerHTML = '';

            for (let i = 0; i < startOffset; i += 1) {
                const emptyCell = document.createElement('div');
                emptyCell.className = 'challenge-calendar__empty is-empty';
                grid.appendChild(emptyCell);
            }

            for (let day = 1; day <= totalDays; day += 1) {
                const cellDate = new Date(year, month, day);
                const dateKey = toDateKey(cellDate);
                const dayPosts = postMap[dateKey] || [];
                const cell = document.createElement('div');
                cell.className = 'challenge-calendar__day';

                if (dateKey === todayKey) {
                    cell.classList.add('is-current');
                }

                if (dayPosts.length > 0) {
                    cell.classList.add('is-active');
                }

                const countHtml = dayPosts.length > 0 ? `<span class="challenge-calendar__count">${dayPosts.length}</span>` : '<span class="challenge-calendar__count">0</span>';
                const dotsHtml = dayPosts.map((post) => `<span class="challenge-calendar__dot ${categoryClass[post.category] || ''}" title="${post.title}"></span>`).join('');
                const visiblePosts = dayPosts.slice(0, 2);
                const moreCount = dayPosts.length - visiblePosts.length;
                const postsHtml = dayPosts.length > 0
                        ? `<div class="challenge-calendar__list">${visiblePosts.map((post) => `<a href="${post.url}" title="${post.categoryLabel}: ${post.title}">${post.categoryLabel}: ${post.title}</a>`).join('')}${moreCount > 0 ? `<span class="challenge-calendar__more">+${moreCount} more</span>` : ''}</div>`
                        : '';

                cell.innerHTML = `
                    <div class="challenge-calendar__date">
                        <span>${day}</span>
                        ${countHtml}
                    </div>
                    <div class="challenge-calendar__dots">${dotsHtml}</div>
                    ${postsHtml}
                `;

                grid.appendChild(cell);
            }
        }

        prevButton.addEventListener('click', () => {
            activeMonth = new Date(activeMonth.getFullYear(), activeMonth.getMonth() - 1, 1);
            renderCalendar();
        });

        nextButton.addEventListener('click', () => {
            activeMonth = new Date(activeMonth.getFullYear(), activeMonth.getMonth() + 1, 1);
            renderCalendar();
        });

        renderCalendar();
    })();
</script>

<hr>

### 📂 Challenge Logs
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div class="card"><div class="card-body">
            <h5 class="card-title">📑 DB Papers</h5>
            <a href="/challenge/db/" class="btn btn-sm z-depth-0" role="button">Go to DB Logs</a>
        </div></div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="card"><div class="card-body">
            <h5 class="card-title">📑 NLP Papers</h5>
            <a href="/challenge/nlp/" class="btn btn-sm z-depth-0" role="button">Go to NLP Logs</a>
        </div></div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="card"><div class="card-body">
            <h5 class="card-title">{% include repo_code_badge.liquid %} Application Practice</h5>
            <a href="/challenge/cloud/" class="btn btn-sm z-depth-0" role="button">Go to Application Practice Logs</a>
        </div></div>
    </div>
</div>
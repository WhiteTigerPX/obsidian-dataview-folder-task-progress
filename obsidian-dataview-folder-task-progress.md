```dataviewjs
const pages = dv.pages('"relative/path/to/your/folder"'); //Must be replaced

let totalTasks = 0;
let completedTasks = 0;

pages.forEach(page => {
  totalTasks += page.file.tasks.length;
  completedTasks += page.file.tasks.filter(task => task.completed).length;
});

if (totalTasks > completedTasks) { // Change to >= to include notes with all tasks completed
  const progress = totalTasks > 0 ? (100 * completedTasks / totalTasks) : 0;

  const textColor = '#555';

  const progressBarHtml = "<div style='display: flex; align-items: center; gap: 15px;'>" +
      "<progress style='width: 90%; height: 12px;' max=100 value=" + progress + "></progress>" +
      "<span style='font-size: 14px; color: " + textColor + "; white-space: nowrap;'>" +
          completedTasks + " / " + totalTasks +
      "</span>" +
  "</div>";

  dv.paragraph(progressBarHtml);
}
```

---
title: 记事本
---

<textarea id="notepad" rows="10" cols="50"></textarea>
<div class="button-container">
    <button id="saveButton" class="custom-button">保存</button>
    <button id="clearButton" class="custom-button clear-button">清空</button>
</div>

<style>
    /* 定义按钮容器的样式 */
  .button-container {
        display: flex;
        justify-content: space-between; /* 使按钮分别位于容器两端 */
        align-items: center;
        margin-top: 10px; /* 与文本区域的间距 */
    }

    /* 定义按钮的通用样式 */
  .custom-button {
        border: none;
        padding: 10px 20px;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }

    /* 保存按钮样式 */
  .custom-button:not(.clear-button) {
        background-color: #007BFF;
        color: white;
    }

    /* 清空按钮样式 */
  .clear-button {
        background-color: #e2e3e5;
        color: #383d41;
    }

    /* 鼠标悬停时按钮的样式 */
  .custom-button:hover {
        filter: brightness(0.9);
    }
</style>

<script>
    // 获取文本区域和按钮元素
    const notepad = document.getElementById('notepad');
    const saveButton = document.getElementById('saveButton');
    const clearButton = document.getElementById('clearButton');

    // 从本地存储中加载笔记
    const savedNote = localStorage.getItem('notepad');
    if (savedNote) {
        notepad.value = savedNote;
    }

    // 保存笔记到本地存储
    saveButton.addEventListener('click', () => {
        const note = notepad.value;
        localStorage.setItem('notepad', note);
        alert('笔记已保存！');
    });

    // 清空笔记
    clearButton.addEventListener('click', () => {
        notepad.value = '';
        localStorage.removeItem('notepad');
        alert('笔记已清空！');
    });
</script>
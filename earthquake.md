---
layout: notebook
title: Earthquake Data Visualisations
description: with Matplotlib and Pandas
---

<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Earthquake_Visualisations</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>




<style type="text/css">
    pre { line-height: 125%; }
td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
.highlight .hll { background-color: var(--jp-cell-editor-active-background) }
.highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
.highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
.highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
.highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
.highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
.highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
.highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
.highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
.highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
.highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
.highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
.highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
.highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
.highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
.highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
.highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
.highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
.highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
.highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
.highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
.highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
.highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
.highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
.highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
.highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
.highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
.highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
.highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
.highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
.highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
.highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
.highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
.highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
.highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
.highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
  </style>



<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
 * Mozilla scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */
[data-jp-theme-scrollbars='true'] {
  scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar. These selectors
 * will match lower in the tree, and so will override the above */
[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
  scrollbar-width: thin;
}

/*
 * Webkit scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-corner {
  background: var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-thumb {
  background: rgb(var(--jp-scrollbar-thumb-color));
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-right: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-bottom: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar */

[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-corner,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-corner {
  background-color: transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-thumb,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid transparent;
  border-right: var(--jp-scrollbar-endpad) solid transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid transparent;
  border-bottom: var(--jp-scrollbar-endpad) solid transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny::-webkit-scrollbar,
.jp-scrollbar-tiny::-webkit-scrollbar-corner {
  background-color: transparent;
  height: 4px;
  width: 4px;
}

.jp-scrollbar-tiny::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:horizontal {
  border-left: 0px solid transparent;
  border-right: 0px solid transparent;
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:vertical {
  border-top: 0px solid transparent;
  border-bottom: 0px solid transparent;
}

/*
 * Phosphor
 */

.lm-ScrollBar[data-orientation='horizontal'] {
  min-height: 16px;
  max-height: 16px;
  min-width: 45px;
  border-top: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] {
  min-width: 16px;
  max-width: 16px;
  min-height: 45px;
  border-left: 1px solid #a0a0a0;
}

.lm-ScrollBar-button {
  background-color: #f0f0f0;
  background-position: center center;
  min-height: 15px;
  max-height: 15px;
  min-width: 15px;
  max-width: 15px;
}

.lm-ScrollBar-button:hover {
  background-color: #dadada;
}

.lm-ScrollBar-button.lm-mod-active {
  background-color: #cdcdcd;
}

.lm-ScrollBar-track {
  background: #f0f0f0;
}

.lm-ScrollBar-thumb {
  background: #cdcdcd;
}

.lm-ScrollBar-thumb:hover {
  background: #bababa;
}

.lm-ScrollBar-thumb.lm-mod-active {
  background: #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
  height: 100%;
  min-width: 15px;
  border-left: 1px solid #a0a0a0;
  border-right: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
  width: 100%;
  min-height: 15px;
  border-top: 1px solid #a0a0a0;
  border-bottom: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-left);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-right);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-up);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-down);
  background-size: 17px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Widget, /* </DEPRECATED> */
.lm-Widget {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  cursor: default;
}


/* <DEPRECATED> */ .p-Widget.p-mod-hidden, /* </DEPRECATED> */
.lm-Widget.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-CommandPalette, /* </DEPRECATED> */
.lm-CommandPalette {
  display: flex;
  flex-direction: column;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-CommandPalette-search, /* </DEPRECATED> */
.lm-CommandPalette-search {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-content, /* </DEPRECATED> */
.lm-CommandPalette-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  min-height: 0;
  overflow: auto;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-CommandPalette-header, /* </DEPRECATED> */
.lm-CommandPalette-header {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}


/* <DEPRECATED> */ .p-CommandPalette-item, /* </DEPRECATED> */
.lm-CommandPalette-item {
  display: flex;
  flex-direction: row;
}


/* <DEPRECATED> */ .p-CommandPalette-itemIcon, /* </DEPRECATED> */
.lm-CommandPalette-itemIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemContent, /* </DEPRECATED> */
.lm-CommandPalette-itemContent {
  flex: 1 1 auto;
  overflow: hidden;
}


/* <DEPRECATED> */ .p-CommandPalette-itemShortcut, /* </DEPRECATED> */
.lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemLabel, /* </DEPRECATED> */
.lm-CommandPalette-itemLabel {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.lm-close-icon {
	border:1px solid transparent;
  background-color: transparent;
  position: absolute;
	z-index:1;
	right:3%;
	top: 0;
	bottom: 0;
	margin: auto;
	padding: 7px 0;
	display: none;
	vertical-align: middle;
  outline: 0;
  cursor: pointer;
}
.lm-close-icon:after {
	content: "X";
	display: block;
	width: 15px;
	height: 15px;
	text-align: center;
	color:#000;
	font-weight: normal;
	font-size: 12px;
	cursor: pointer;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-DockPanel, /* </DEPRECATED> */
.lm-DockPanel {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-widget, /* </DEPRECATED> */
.lm-DockPanel-widget {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-tabBar, /* </DEPRECATED> */
.lm-DockPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-DockPanel-handle, /* </DEPRECATED> */
.lm-DockPanel-handle {
  z-index: 2;
}


/* <DEPRECATED> */ .p-DockPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-DockPanel-handle:after, /* </DEPRECATED> */
.lm-DockPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal'] {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical'] {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal']:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical']:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}


/* <DEPRECATED> */ .p-DockPanel-overlay, /* </DEPRECATED> */
.lm-DockPanel-overlay {
  z-index: 3;
  box-sizing: border-box;
  pointer-events: none;
}


/* <DEPRECATED> */ .p-DockPanel-overlay.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-overlay.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Menu, /* </DEPRECATED> */
.lm-Menu {
  z-index: 10000;
  position: absolute;
  white-space: nowrap;
  overflow-x: hidden;
  overflow-y: auto;
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-Menu-content, /* </DEPRECATED> */
.lm-Menu-content {
  margin: 0;
  padding: 0;
  display: table;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-Menu-item, /* </DEPRECATED> */
.lm-Menu-item {
  display: table-row;
}


/* <DEPRECATED> */
.p-Menu-item.p-mod-hidden,
.p-Menu-item.p-mod-collapsed,
/* </DEPRECATED> */
.lm-Menu-item.lm-mod-hidden,
.lm-Menu-item.lm-mod-collapsed {
  display: none !important;
}


/* <DEPRECATED> */
.p-Menu-itemIcon,
.p-Menu-itemSubmenuIcon,
/* </DEPRECATED> */
.lm-Menu-itemIcon,
.lm-Menu-itemSubmenuIcon {
  display: table-cell;
  text-align: center;
}


/* <DEPRECATED> */ .p-Menu-itemLabel, /* </DEPRECATED> */
.lm-Menu-itemLabel {
  display: table-cell;
  text-align: left;
}


/* <DEPRECATED> */ .p-Menu-itemShortcut, /* </DEPRECATED> */
.lm-Menu-itemShortcut {
  display: table-cell;
  text-align: right;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-MenuBar, /* </DEPRECATED> */
.lm-MenuBar {
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-MenuBar-content, /* </DEPRECATED> */
.lm-MenuBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: row;
  list-style-type: none;
}


/* <DEPRECATED> */ .p--MenuBar-item, /* </DEPRECATED> */
.lm-MenuBar-item {
  box-sizing: border-box;
}


/* <DEPRECATED> */
.p-MenuBar-itemIcon,
.p-MenuBar-itemLabel,
/* </DEPRECATED> */
.lm-MenuBar-itemIcon,
.lm-MenuBar-itemLabel {
  display: inline-block;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-ScrollBar, /* </DEPRECATED> */
.lm-ScrollBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='horizontal'] {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='vertical'] {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-ScrollBar-button, /* </DEPRECATED> */
.lm-ScrollBar-button {
  box-sizing: border-box;
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-track, /* </DEPRECATED> */
.lm-ScrollBar-track {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  flex: 1 1 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-thumb, /* </DEPRECATED> */
.lm-ScrollBar-thumb {
  box-sizing: border-box;
  position: absolute;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-SplitPanel-child, /* </DEPRECATED> */
.lm-SplitPanel-child {
  z-index: 0;
}


/* <DEPRECATED> */ .p-SplitPanel-handle, /* </DEPRECATED> */
.lm-SplitPanel-handle {
  z-index: 1;
}


/* <DEPRECATED> */ .p-SplitPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-SplitPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-SplitPanel-handle:after, /* </DEPRECATED> */
.lm-SplitPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabBar, /* </DEPRECATED> */
.lm-TabBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='horizontal'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] {
  flex-direction: row;
  align-items: flex-end;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='vertical'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] {
  flex-direction: column;
  align-items: flex-end;
}


/* <DEPRECATED> */ .p-TabBar-content, /* </DEPRECATED> */
.lm-TabBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex: 1 1 auto;
  list-style-type: none;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='horizontal'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='vertical'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar-tab {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  overflow: hidden;
}


/* <DEPRECATED> */
.p-TabBar-tabIcon,
.p-TabBar-tabCloseIcon,
/* </DEPRECATED> */
.lm-TabBar-tabIcon,
.lm-TabBar-tabCloseIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-TabBar-tabLabel, /* </DEPRECATED> */
.lm-TabBar-tabLabel {
  flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}


.lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing : border-box;
}


/* <DEPRECATED> */ .p-TabBar-tab.p-mod-hidden, /* </DEPRECATED> */
.lm-TabBar-tab.lm-mod-hidden {
  display: none !important;
}


.lm-TabBar-addButton.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-TabBar.p-mod-dragging .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
  position: relative;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='horizontal'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
  left: 0;
  transition: left 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='vertical'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
  top: 0;
  transition: top 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging .p-TabBar-tab.p-mod-dragging,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
  transition: none;
}

.lm-TabBar-tabLabel .lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing : border-box;
  background: inherit;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabPanel-tabBar, /* </DEPRECATED> */
.lm-TabPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-TabPanel-stackedPanel, /* </DEPRECATED> */
.lm-TabPanel-stackedPanel {
  z-index: 0;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

@charset "UTF-8";
html{
  -webkit-box-sizing:border-box;
          box-sizing:border-box; }

*,
*::before,
*::after{
  -webkit-box-sizing:inherit;
          box-sizing:inherit; }

body{
  font-size:14px;
  font-weight:400;
  letter-spacing:0;
  line-height:1.28581;
  text-transform:none;
  color:#182026;
  font-family:-apple-system, "BlinkMacSystemFont", "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Open Sans", "Helvetica Neue", "Icons16", sans-serif; }

p{
  margin-bottom:10px;
  margin-top:0; }

small{
  font-size:12px; }

strong{
  font-weight:600; }

::-moz-selection{
  background:rgba(125, 188, 255, 0.6); }

::selection{
  background:rgba(125, 188, 255, 0.6); }
.bp3-heading{
  color:#182026;
  font-weight:600;
  margin:0 0 10px;
  padding:0; }
  .bp3-dark .bp3-heading{
    color:#f5f8fa; }

h1.bp3-heading, .bp3-running-text h1{
  font-size:36px;
  line-height:40px; }

h2.bp3-heading, .bp3-running-text h2{
  font-size:28px;
  line-height:32px; }

h3.bp3-heading, .bp3-running-text h3{
  font-size:22px;
  line-height:25px; }

h4.bp3-heading, .bp3-running-text h4{
  font-size:18px;
  line-height:21px; }

h5.bp3-heading, .bp3-running-text h5{
  font-size:16px;
  line-height:19px; }

h6.bp3-heading, .bp3-running-text h6{
  font-size:14px;
  line-height:16px; }
.bp3-ui-text{
  font-size:14px;
  font-weight:400;
  letter-spacing:0;
  line-height:1.28581;
  text-transform:none; }

.bp3-monospace-text{
  font-family:monospace;
  text-transform:none; }

.bp3-text-muted{
  color:#5c7080; }
  .bp3-dark .bp3-text-muted{
    color:#a7b6c2; }

.bp3-text-disabled{
  color:rgba(92, 112, 128, 0.6); }
  .bp3-dark .bp3-text-disabled{
    color:rgba(167, 182, 194, 0.6); }

.bp3-text-overflow-ellipsis{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal; }
.bp3-running-text{
  font-size:14px;
  line-height:1.5; }
  .bp3-running-text h1{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h1{
      color:#f5f8fa; }
  .bp3-running-text h2{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h2{
      color:#f5f8fa; }
  .bp3-running-text h3{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h3{
      color:#f5f8fa; }
  .bp3-running-text h4{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h4{
      color:#f5f8fa; }
  .bp3-running-text h5{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h5{
      color:#f5f8fa; }
  .bp3-running-text h6{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h6{
      color:#f5f8fa; }
  .bp3-running-text hr{
    border:none;
    border-bottom:1px solid rgba(16, 22, 26, 0.15);
    margin:20px 0; }
    .bp3-dark .bp3-running-text hr{
      border-color:rgba(255, 255, 255, 0.15); }
  .bp3-running-text p{
    margin:0 0 10px;
    padding:0; }

.bp3-text-large{
  font-size:16px; }

.bp3-text-small{
  font-size:12px; }
a{
  color:#106ba3;
  text-decoration:none; }
  a:hover{
    color:#106ba3;
    cursor:pointer;
    text-decoration:underline; }
  a .bp3-icon, a .bp3-icon-standard, a .bp3-icon-large{
    color:inherit; }
  a code,
  .bp3-dark a code{
    color:inherit; }
  .bp3-dark a,
  .bp3-dark a:hover{
    color:#48aff0; }
    .bp3-dark a .bp3-icon, .bp3-dark a .bp3-icon-standard, .bp3-dark a .bp3-icon-large,
    .bp3-dark a:hover .bp3-icon,
    .bp3-dark a:hover .bp3-icon-standard,
    .bp3-dark a:hover .bp3-icon-large{
      color:inherit; }
.bp3-running-text code, .bp3-code{
  font-family:monospace;
  text-transform:none;
  background:rgba(255, 255, 255, 0.7);
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
  color:#5c7080;
  font-size:smaller;
  padding:2px 5px; }
  .bp3-dark .bp3-running-text code, .bp3-running-text .bp3-dark code, .bp3-dark .bp3-code{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#a7b6c2; }
  .bp3-running-text a > code, a > .bp3-code{
    color:#137cbd; }
    .bp3-dark .bp3-running-text a > code, .bp3-running-text .bp3-dark a > code, .bp3-dark a > .bp3-code{
      color:inherit; }

.bp3-running-text pre, .bp3-code-block{
  font-family:monospace;
  text-transform:none;
  background:rgba(255, 255, 255, 0.7);
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
  color:#182026;
  display:block;
  font-size:13px;
  line-height:1.4;
  margin:10px 0;
  padding:13px 15px 12px;
  word-break:break-all;
  word-wrap:break-word; }
  .bp3-dark .bp3-running-text pre, .bp3-running-text .bp3-dark pre, .bp3-dark .bp3-code-block{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
  .bp3-running-text pre > code, .bp3-code-block > code{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:inherit;
    font-size:inherit;
    padding:0; }

.bp3-running-text kbd, .bp3-key{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#5c7080;
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  font-family:inherit;
  font-size:12px;
  height:24px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  line-height:24px;
  min-width:24px;
  padding:3px 6px;
  vertical-align:middle; }
  .bp3-running-text kbd .bp3-icon, .bp3-key .bp3-icon, .bp3-running-text kbd .bp3-icon-standard, .bp3-key .bp3-icon-standard, .bp3-running-text kbd .bp3-icon-large, .bp3-key .bp3-icon-large{
    margin-right:5px; }
  .bp3-dark .bp3-running-text kbd, .bp3-running-text .bp3-dark kbd, .bp3-dark .bp3-key{
    background:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#a7b6c2; }
.bp3-running-text blockquote, .bp3-blockquote{
  border-left:solid 4px rgba(167, 182, 194, 0.5);
  margin:0 0 10px;
  padding:0 20px; }
  .bp3-dark .bp3-running-text blockquote, .bp3-running-text .bp3-dark blockquote, .bp3-dark .bp3-blockquote{
    border-color:rgba(115, 134, 148, 0.5); }
.bp3-running-text ul,
.bp3-running-text ol, .bp3-list{
  margin:10px 0;
  padding-left:30px; }
  .bp3-running-text ul li:not(:last-child), .bp3-running-text ol li:not(:last-child), .bp3-list li:not(:last-child){
    margin-bottom:5px; }
  .bp3-running-text ul ol, .bp3-running-text ol ol, .bp3-list ol,
  .bp3-running-text ul ul,
  .bp3-running-text ol ul,
  .bp3-list ul{
    margin-top:5px; }

.bp3-list-unstyled{
  list-style:none;
  margin:0;
  padding:0; }
  .bp3-list-unstyled li{
    padding:0; }
.bp3-rtl{
  text-align:right; }

.bp3-dark{
  color:#f5f8fa; }

:focus{
  outline:rgba(19, 124, 189, 0.6) auto 2px;
  outline-offset:2px;
  -moz-outline-radius:6px; }

.bp3-focus-disabled :focus{
  outline:none !important; }
  .bp3-focus-disabled :focus ~ .bp3-control-indicator{
    outline:none !important; }

.bp3-alert{
  max-width:400px;
  padding:20px; }

.bp3-alert-body{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-alert-body .bp3-icon{
    font-size:40px;
    margin-right:20px;
    margin-top:0; }

.bp3-alert-contents{
  word-break:break-word; }

.bp3-alert-footer{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:reverse;
      -ms-flex-direction:row-reverse;
          flex-direction:row-reverse;
  margin-top:10px; }
  .bp3-alert-footer .bp3-button{
    margin-left:10px; }
.bp3-breadcrumbs{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  cursor:default;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:wrap;
      flex-wrap:wrap;
  height:30px;
  list-style:none;
  margin:0;
  padding:0; }
  .bp3-breadcrumbs > li{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }
    .bp3-breadcrumbs > li::after{
      background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M10.71 7.29l-4-4a1.003 1.003 0 00-1.42 1.42L8.59 8 5.3 11.29c-.19.18-.3.43-.3.71a1.003 1.003 0 001.71.71l4-4c.18-.18.29-.43.29-.71 0-.28-.11-.53-.29-.71z' fill='%235C7080'/%3e%3c/svg%3e");
      content:"";
      display:block;
      height:16px;
      margin:0 5px;
      width:16px; }
    .bp3-breadcrumbs > li:last-of-type::after{
      display:none; }

.bp3-breadcrumb,
.bp3-breadcrumb-current,
.bp3-breadcrumbs-collapsed{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  font-size:16px; }

.bp3-breadcrumb,
.bp3-breadcrumbs-collapsed{
  color:#5c7080; }

.bp3-breadcrumb:hover{
  text-decoration:none; }

.bp3-breadcrumb.bp3-disabled{
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-breadcrumb .bp3-icon{
  margin-right:5px; }

.bp3-breadcrumb-current{
  color:inherit;
  font-weight:600; }
  .bp3-breadcrumb-current .bp3-input{
    font-size:inherit;
    font-weight:inherit;
    vertical-align:baseline; }

.bp3-breadcrumbs-collapsed{
  background:#ced9e0;
  border:none;
  border-radius:3px;
  cursor:pointer;
  margin-right:2px;
  padding:1px 5px;
  vertical-align:text-bottom; }
  .bp3-breadcrumbs-collapsed::before{
    background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cg fill='%235C7080'%3e%3ccircle cx='2' cy='8.03' r='2'/%3e%3ccircle cx='14' cy='8.03' r='2'/%3e%3ccircle cx='8' cy='8.03' r='2'/%3e%3c/g%3e%3c/svg%3e") center no-repeat;
    content:"";
    display:block;
    height:16px;
    width:16px; }
  .bp3-breadcrumbs-collapsed:hover{
    background:#bfccd6;
    color:#182026;
    text-decoration:none; }

.bp3-dark .bp3-breadcrumb,
.bp3-dark .bp3-breadcrumbs-collapsed{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumbs > li::after{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumb.bp3-disabled{
  color:rgba(167, 182, 194, 0.6); }

.bp3-dark .bp3-breadcrumb-current{
  color:#f5f8fa; }

.bp3-dark .bp3-breadcrumbs-collapsed{
  background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-breadcrumbs-collapsed:hover{
    background:rgba(16, 22, 26, 0.6);
    color:#f5f8fa; }
.bp3-button{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  font-size:14px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  padding:5px 10px;
  text-align:left;
  vertical-align:middle;
  min-height:30px;
  min-width:30px; }
  .bp3-button > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-button > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-button::before,
  .bp3-button > *{
    margin-right:7px; }
  .bp3-button:empty::before,
  .bp3-button > :last-child{
    margin-right:0; }
  .bp3-button:empty{
    padding:0 !important; }
  .bp3-button:disabled, .bp3-button.bp3-disabled{
    cursor:not-allowed; }
  .bp3-button.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button.bp3-align-right,
  .bp3-align-right .bp3-button{
    text-align:right; }
  .bp3-button.bp3-align-left,
  .bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-button:not([class*="bp3-intent-"]){
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026; }
    .bp3-button:not([class*="bp3-intent-"]):hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-button:not([class*="bp3-intent-"]):active, .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active:hover, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-button.bp3-intent-primary{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover, .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover{
      background-color:#106ba3;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      background-color:#0e5a8a;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-primary:disabled, .bp3-button.bp3-intent-primary.bp3-disabled{
      background-color:rgba(19, 124, 189, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-success{
    background-color:#0f9960;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-success:hover, .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-success:hover{
      background-color:#0d8050;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      background-color:#0a6640;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-success:disabled, .bp3-button.bp3-intent-success.bp3-disabled{
      background-color:rgba(15, 153, 96, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-warning{
    background-color:#d9822b;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover, .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover{
      background-color:#bf7326;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      background-color:#a66321;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-warning:disabled, .bp3-button.bp3-intent-warning.bp3-disabled{
      background-color:rgba(217, 130, 43, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-danger{
    background-color:#db3737;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover, .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover{
      background-color:#c23030;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      background-color:#a82a2a;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-danger:disabled, .bp3-button.bp3-intent-danger.bp3-disabled{
      background-color:rgba(219, 55, 55, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
    stroke:#ffffff; }
  .bp3-button.bp3-large,
  .bp3-large .bp3-button{
    min-height:40px;
    min-width:40px;
    font-size:16px;
    padding:5px 15px; }
    .bp3-button.bp3-large::before,
    .bp3-button.bp3-large > *,
    .bp3-large .bp3-button::before,
    .bp3-large .bp3-button > *{
      margin-right:10px; }
    .bp3-button.bp3-large:empty::before,
    .bp3-button.bp3-large > :last-child,
    .bp3-large .bp3-button:empty::before,
    .bp3-large .bp3-button > :last-child{
      margin-right:0; }
  .bp3-button.bp3-small,
  .bp3-small .bp3-button{
    min-height:24px;
    min-width:24px;
    padding:0 7px; }
  .bp3-button.bp3-loading{
    position:relative; }
    .bp3-button.bp3-loading[class*="bp3-icon-"]::before{
      visibility:hidden; }
    .bp3-button.bp3-loading .bp3-button-spinner{
      margin:0;
      position:absolute; }
    .bp3-button.bp3-loading > :not(.bp3-button-spinner){
      visibility:hidden; }
  .bp3-button[class*="bp3-icon-"]::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    color:#5c7080; }
  .bp3-button .bp3-icon, .bp3-button .bp3-icon-standard, .bp3-button .bp3-icon-large{
    color:#5c7080; }
    .bp3-button .bp3-icon.bp3-align-right, .bp3-button .bp3-icon-standard.bp3-align-right, .bp3-button .bp3-icon-large.bp3-align-right{
      margin-left:7px; }
  .bp3-button .bp3-icon:first-child:last-child,
  .bp3-button .bp3-spinner + .bp3-icon:last-child{
    margin:0 -7px; }
  .bp3-dark .bp3-button:not([class*="bp3-intent-"]){
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover, .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"])[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-large{
      color:#a7b6c2; }
  .bp3-dark .bp3-button[class*="bp3-intent-"]{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:hover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:active, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-active{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:disabled, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-disabled{
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.3); }
    .bp3-dark .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
      stroke:#8a9ba8; }
  .bp3-button:disabled::before,
  .bp3-button:disabled .bp3-icon, .bp3-button:disabled .bp3-icon-standard, .bp3-button:disabled .bp3-icon-large, .bp3-button.bp3-disabled::before,
  .bp3-button.bp3-disabled .bp3-icon, .bp3-button.bp3-disabled .bp3-icon-standard, .bp3-button.bp3-disabled .bp3-icon-large, .bp3-button[class*="bp3-intent-"]::before,
  .bp3-button[class*="bp3-intent-"] .bp3-icon, .bp3-button[class*="bp3-intent-"] .bp3-icon-standard, .bp3-button[class*="bp3-intent-"] .bp3-icon-large{
    color:inherit !important; }
  .bp3-button.bp3-minimal{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-button.bp3-minimal:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button.bp3-minimal:active, .bp3-button.bp3-minimal.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button.bp3-minimal:disabled, .bp3-button.bp3-minimal:disabled:hover, .bp3-button.bp3-minimal.bp3-disabled, .bp3-button.bp3-minimal.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button.bp3-minimal{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button.bp3-minimal:hover, .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button.bp3-minimal:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button.bp3-minimal:disabled, .bp3-dark .bp3-button.bp3-minimal:disabled:hover, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover, .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-success{
      color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover, .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover, .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-danger{
      color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover, .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
  .bp3-button.bp3-outlined{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    border:1px solid rgba(24, 32, 38, 0.2);
    -webkit-box-sizing:border-box;
            box-sizing:border-box; }
    .bp3-button.bp3-outlined:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button.bp3-outlined:active, .bp3-button.bp3-outlined.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button.bp3-outlined{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button.bp3-outlined:hover, .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button.bp3-outlined:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:hover, .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-success{
      color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:hover, .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:hover, .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-danger{
      color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:hover, .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
    .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled:hover{
      border-color:rgba(92, 112, 128, 0.1); }
    .bp3-dark .bp3-button.bp3-outlined{
      border-color:rgba(255, 255, 255, 0.4); }
      .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
        border-color:rgba(255, 255, 255, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-primary{
      border-color:rgba(16, 107, 163, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
        border-color:rgba(16, 107, 163, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
        border-color:rgba(72, 175, 240, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          border-color:rgba(72, 175, 240, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-success{
      border-color:rgba(13, 128, 80, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
        border-color:rgba(13, 128, 80, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
        border-color:rgba(61, 204, 145, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          border-color:rgba(61, 204, 145, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-warning{
      border-color:rgba(191, 115, 38, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
        border-color:rgba(191, 115, 38, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
        border-color:rgba(255, 179, 102, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          border-color:rgba(255, 179, 102, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-danger{
      border-color:rgba(194, 48, 48, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
        border-color:rgba(194, 48, 48, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
        border-color:rgba(255, 115, 115, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          border-color:rgba(255, 115, 115, 0.2); }

a.bp3-button{
  text-align:center;
  text-decoration:none;
  -webkit-transition:none;
  transition:none; }
  a.bp3-button, a.bp3-button:hover, a.bp3-button:active{
    color:#182026; }
  a.bp3-button.bp3-disabled{
    color:rgba(92, 112, 128, 0.6); }

.bp3-button-text{
  -webkit-box-flex:0;
      -ms-flex:0 1 auto;
          flex:0 1 auto; }

.bp3-button.bp3-align-left .bp3-button-text, .bp3-button.bp3-align-right .bp3-button-text,
.bp3-button-group.bp3-align-left .bp3-button-text,
.bp3-button-group.bp3-align-right .bp3-button-text{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto; }
.bp3-button-group{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex; }
  .bp3-button-group .bp3-button{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    position:relative;
    z-index:4; }
    .bp3-button-group .bp3-button:focus{
      z-index:5; }
    .bp3-button-group .bp3-button:hover{
      z-index:6; }
    .bp3-button-group .bp3-button:active, .bp3-button-group .bp3-button.bp3-active{
      z-index:7; }
    .bp3-button-group .bp3-button:disabled, .bp3-button-group .bp3-button.bp3-disabled{
      z-index:3; }
    .bp3-button-group .bp3-button[class*="bp3-intent-"]{
      z-index:9; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:focus{
        z-index:10; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:hover{
        z-index:11; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:active, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-active{
        z-index:12; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:disabled, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-disabled{
        z-index:8; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:first-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:first-child){
    border-bottom-left-radius:0;
    border-top-left-radius:0; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    border-bottom-right-radius:0;
    border-top-right-radius:0;
    margin-right:-1px; }
  .bp3-button-group.bp3-minimal .bp3-button{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-button-group.bp3-minimal .bp3-button:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button-group.bp3-minimal .bp3-button{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
      color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
      color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
  .bp3-button-group .bp3-popover-wrapper,
  .bp3-button-group .bp3-popover-target{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button-group .bp3-button.bp3-fill,
  .bp3-button-group.bp3-fill .bp3-button:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-vertical{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    vertical-align:top; }
    .bp3-button-group.bp3-vertical.bp3-fill{
      height:100%;
      width:unset; }
    .bp3-button-group.bp3-vertical .bp3-button{
      margin-right:0 !important;
      width:100%; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:first-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:first-child{
      border-radius:3px 3px 0 0; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:last-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:last-child{
      border-radius:0 0 3px 3px; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:not(:last-child){
      margin-bottom:-1px; }
  .bp3-button-group.bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    margin-right:1px; }
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-button:not(:last-child){
    margin-bottom:1px; }
.bp3-callout{
  font-size:14px;
  line-height:1.5;
  background-color:rgba(138, 155, 168, 0.15);
  border-radius:3px;
  padding:10px 12px 9px;
  position:relative;
  width:100%; }
  .bp3-callout[class*="bp3-icon-"]{
    padding-left:40px; }
    .bp3-callout[class*="bp3-icon-"]::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      color:#5c7080;
      left:10px;
      position:absolute;
      top:10px; }
  .bp3-callout.bp3-callout-icon{
    padding-left:40px; }
    .bp3-callout.bp3-callout-icon > .bp3-icon:first-child{
      color:#5c7080;
      left:10px;
      position:absolute;
      top:10px; }
  .bp3-callout .bp3-heading{
    line-height:20px;
    margin-bottom:5px;
    margin-top:0; }
    .bp3-callout .bp3-heading:last-child{
      margin-bottom:0; }
  .bp3-dark .bp3-callout{
    background-color:rgba(138, 155, 168, 0.2); }
    .bp3-dark .bp3-callout[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
  .bp3-callout.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15); }
    .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-primary .bp3-heading{
      color:#106ba3; }
    .bp3-dark .bp3-callout.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-primary .bp3-heading{
        color:#48aff0; }
  .bp3-callout.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15); }
    .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-success .bp3-heading{
      color:#0d8050; }
    .bp3-dark .bp3-callout.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-success .bp3-heading{
        color:#3dcc91; }
  .bp3-callout.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15); }
    .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-warning .bp3-heading{
      color:#bf7326; }
    .bp3-dark .bp3-callout.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-warning .bp3-heading{
        color:#ffb366; }
  .bp3-callout.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15); }
    .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-danger .bp3-heading{
      color:#c23030; }
    .bp3-dark .bp3-callout.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-danger .bp3-heading{
        color:#ff7373; }
  .bp3-running-text .bp3-callout{
    margin:20px 0; }
.bp3-card{
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
  padding:20px;
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-card.bp3-dark,
  .bp3-dark .bp3-card{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

.bp3-elevation-0{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }
  .bp3-elevation-0.bp3-dark,
  .bp3-dark .bp3-elevation-0{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

.bp3-elevation-1{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-1.bp3-dark,
  .bp3-dark .bp3-elevation-1{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-elevation-2{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-2.bp3-dark,
  .bp3-dark .bp3-elevation-2{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4); }

.bp3-elevation-3{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-3.bp3-dark,
  .bp3-dark .bp3-elevation-3{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-elevation-4{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-4.bp3-dark,
  .bp3-dark .bp3-elevation-4{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:hover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  cursor:pointer; }
  .bp3-card.bp3-interactive:hover.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:hover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:active{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  opacity:0.9;
  -webkit-transition-duration:0;
          transition-duration:0; }
  .bp3-card.bp3-interactive:active.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:active{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-collapse{
  height:0;
  overflow-y:hidden;
  -webkit-transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-collapse .bp3-collapse-body{
    -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-collapse .bp3-collapse-body[aria-hidden="true"]{
      display:none; }

.bp3-context-menu .bp3-popover-target{
  display:block; }

.bp3-context-menu-popover-target{
  position:fixed; }

.bp3-divider{
  border-bottom:1px solid rgba(16, 22, 26, 0.15);
  border-right:1px solid rgba(16, 22, 26, 0.15);
  margin:5px; }
  .bp3-dark .bp3-divider{
    border-color:rgba(16, 22, 26, 0.4); }
.bp3-dialog-container{
  opacity:1;
  -webkit-transform:scale(1);
          transform:scale(1);
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  min-height:100%;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none;
  width:100%; }
  .bp3-dialog-container.bp3-overlay-enter > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5); }
  .bp3-dialog-container.bp3-overlay-enter-active > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear-active > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-dialog-container.bp3-overlay-exit > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-dialog-container.bp3-overlay-exit-active > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }

.bp3-dialog{
  background:#ebf1f5;
  border-radius:6px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:30px 0;
  padding-bottom:20px;
  pointer-events:all;
  -webkit-user-select:text;
     -moz-user-select:text;
      -ms-user-select:text;
          user-select:text;
  width:500px; }
  .bp3-dialog:focus{
    outline:0; }
  .bp3-dialog.bp3-dark,
  .bp3-dark .bp3-dialog{
    background:#293742;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }

.bp3-dialog-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background:#ffffff;
  border-radius:6px 6px 0 0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  min-height:40px;
  padding-left:20px;
  padding-right:5px;
  z-index:30; }
  .bp3-dialog-header .bp3-icon-large,
  .bp3-dialog-header .bp3-icon{
    color:#5c7080;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px; }
  .bp3-dialog-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:inherit;
    margin:0; }
    .bp3-dialog-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-dialog-header{
    background:#30404d;
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-dialog-header .bp3-icon-large,
    .bp3-dark .bp3-dialog-header .bp3-icon{
      color:#a7b6c2; }

.bp3-dialog-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  line-height:18px;
  margin:20px; }

.bp3-dialog-footer{
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  margin:0 20px; }

.bp3-dialog-footer-actions{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:end;
      -ms-flex-pack:end;
          justify-content:flex-end; }
  .bp3-dialog-footer-actions .bp3-button{
    margin-left:10px; }
.bp3-multistep-dialog-panels{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }

.bp3-multistep-dialog-left-panel{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:1;
      -ms-flex:1;
          flex:1;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column; }
  .bp3-dark .bp3-multistep-dialog-left-panel{
    background:#202b33; }

.bp3-multistep-dialog-right-panel{
  background-color:#f5f8fa;
  border-left:1px solid rgba(16, 22, 26, 0.15);
  border-radius:0 0 6px 0;
  -webkit-box-flex:3;
      -ms-flex:3;
          flex:3;
  min-width:0; }
  .bp3-dark .bp3-multistep-dialog-right-panel{
    background-color:#293742;
    border-left:1px solid rgba(16, 22, 26, 0.4); }

.bp3-multistep-dialog-footer{
  background-color:#ffffff;
  border-radius:0 0 6px 0;
  border-top:1px solid rgba(16, 22, 26, 0.15);
  padding:10px; }
  .bp3-dark .bp3-multistep-dialog-footer{
    background:#30404d;
    border-top:1px solid rgba(16, 22, 26, 0.4); }

.bp3-dialog-step-container{
  background-color:#f5f8fa;
  border-bottom:1px solid rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-dialog-step-container{
    background:#293742;
    border-bottom:1px solid rgba(16, 22, 26, 0.4); }
  .bp3-dialog-step-container.bp3-dialog-step-viewed{
    background-color:#ffffff; }
    .bp3-dark .bp3-dialog-step-container.bp3-dialog-step-viewed{
      background:#30404d; }

.bp3-dialog-step{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:#f5f8fa;
  border-radius:6px;
  cursor:not-allowed;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin:4px;
  padding:6px 14px; }
  .bp3-dark .bp3-dialog-step{
    background:#293742; }
  .bp3-dialog-step-viewed .bp3-dialog-step{
    background-color:#ffffff;
    cursor:pointer; }
    .bp3-dark .bp3-dialog-step-viewed .bp3-dialog-step{
      background:#30404d; }
  .bp3-dialog-step:hover{
    background-color:#f5f8fa; }
    .bp3-dark .bp3-dialog-step:hover{
      background:#293742; }

.bp3-dialog-step-icon{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:rgba(92, 112, 128, 0.6);
  border-radius:50%;
  color:#ffffff;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:25px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  width:25px; }
  .bp3-dark .bp3-dialog-step-icon{
    background-color:rgba(167, 182, 194, 0.6); }
  .bp3-active.bp3-dialog-step-viewed .bp3-dialog-step-icon{
    background-color:#2b95d6; }
  .bp3-dialog-step-viewed .bp3-dialog-step-icon{
    background-color:#8a9ba8; }

.bp3-dialog-step-title{
  color:rgba(92, 112, 128, 0.6);
  -webkit-box-flex:1;
      -ms-flex:1;
          flex:1;
  padding-left:10px; }
  .bp3-dark .bp3-dialog-step-title{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-active.bp3-dialog-step-viewed .bp3-dialog-step-title{
    color:#2b95d6; }
  .bp3-dialog-step-viewed:not(.bp3-active) .bp3-dialog-step-title{
    color:#182026; }
    .bp3-dark .bp3-dialog-step-viewed:not(.bp3-active) .bp3-dialog-step-title{
      color:#f5f8fa; }
.bp3-drawer{
  background:#ffffff;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0;
  padding:0; }
  .bp3-drawer:focus{
    outline:0; }
  .bp3-drawer.bp3-position-top{
    height:50%;
    left:0;
    right:0;
    top:0; }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter, .bp3-drawer.bp3-position-top.bp3-overlay-appear{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%); }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter-active, .bp3-drawer.bp3-position-top.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit-active{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-bottom{
    bottom:0;
    height:50%;
    left:0;
    right:0; }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter-active, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-left{
    bottom:0;
    left:0;
    top:0;
    width:50%; }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter, .bp3-drawer.bp3-position-left.bp3-overlay-appear{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%); }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter-active, .bp3-drawer.bp3-position-left.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit-active{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-right{
    bottom:0;
    right:0;
    top:0;
    width:50%; }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter, .bp3-drawer.bp3-position-right.bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter-active, .bp3-drawer.bp3-position-right.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right):not(.bp3-vertical){
    bottom:0;
    right:0;
    top:0;
    width:50%; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right).bp3-vertical{
    bottom:0;
    height:50%;
    left:0;
    right:0; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-dark,
  .bp3-dark .bp3-drawer{
    background:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }

.bp3-drawer-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border-radius:0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  min-height:40px;
  padding:5px;
  padding-left:20px;
  position:relative; }
  .bp3-drawer-header .bp3-icon-large,
  .bp3-drawer-header .bp3-icon{
    color:#5c7080;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px; }
  .bp3-drawer-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:inherit;
    margin:0; }
    .bp3-drawer-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-drawer-header{
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-drawer-header .bp3-icon-large,
    .bp3-dark .bp3-drawer-header .bp3-icon{
      color:#a7b6c2; }

.bp3-drawer-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  line-height:18px;
  overflow:auto; }

.bp3-drawer-footer{
  -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  padding:10px 20px;
  position:relative; }
  .bp3-dark .bp3-drawer-footer{
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4); }
.bp3-editable-text{
  cursor:text;
  display:inline-block;
  max-width:100%;
  position:relative;
  vertical-align:top;
  white-space:nowrap; }
  .bp3-editable-text::before{
    bottom:-3px;
    left:-3px;
    position:absolute;
    right:-3px;
    top:-3px;
    border-radius:3px;
    content:"";
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-editable-text.bp3-editable-text-editing::before{
    background-color:#ffffff;
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#137cbd; }
  .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4); }
  .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#0f9960; }
  .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4); }
  .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#d9822b; }
  .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4); }
  .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#db3737; }
  .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4); }
  .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15); }
  .bp3-dark .bp3-editable-text.bp3-editable-text-editing::before{
    background-color:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#48aff0; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4);
            box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#3dcc91; }
  .bp3-dark .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4);
            box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#ffb366; }
  .bp3-dark .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4);
            box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#ff7373; }
  .bp3-dark .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4);
            box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-editable-text-input,
.bp3-editable-text-content{
  color:inherit;
  display:inherit;
  font:inherit;
  letter-spacing:inherit;
  max-width:inherit;
  min-width:inherit;
  position:relative;
  resize:none;
  text-transform:inherit;
  vertical-align:top; }

.bp3-editable-text-input{
  background:none;
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0;
  white-space:pre-wrap;
  width:100%; }
  .bp3-editable-text-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input:focus{
    outline:none; }
  .bp3-editable-text-input::-ms-clear{
    display:none; }

.bp3-editable-text-content{
  overflow:hidden;
  padding-right:2px;
  text-overflow:ellipsis;
  white-space:pre; }
  .bp3-editable-text-editing > .bp3-editable-text-content{
    left:0;
    position:absolute;
    visibility:hidden; }
  .bp3-editable-text-placeholder > .bp3-editable-text-content{
    color:rgba(92, 112, 128, 0.6); }
    .bp3-dark .bp3-editable-text-placeholder > .bp3-editable-text-content{
      color:rgba(167, 182, 194, 0.6); }

.bp3-editable-text.bp3-multiline{
  display:block; }
  .bp3-editable-text.bp3-multiline .bp3-editable-text-content{
    overflow:auto;
    white-space:pre-wrap;
    word-wrap:break-word; }
.bp3-divider{
  border-bottom:1px solid rgba(16, 22, 26, 0.15);
  border-right:1px solid rgba(16, 22, 26, 0.15);
  margin:5px; }
  .bp3-dark .bp3-divider{
    border-color:rgba(16, 22, 26, 0.4); }
.bp3-control-group{
  -webkit-transform:translateZ(0);
          transform:translateZ(0);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:stretch;
      -ms-flex-align:stretch;
          align-items:stretch; }
  .bp3-control-group > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select,
  .bp3-control-group .bp3-input,
  .bp3-control-group .bp3-select{
    position:relative; }
  .bp3-control-group .bp3-input{
    border-radius:inherit;
    z-index:2; }
    .bp3-control-group .bp3-input:focus{
      border-radius:3px;
      z-index:14; }
    .bp3-control-group .bp3-input[class*="bp3-intent"]{
      z-index:13; }
      .bp3-control-group .bp3-input[class*="bp3-intent"]:focus{
        z-index:15; }
    .bp3-control-group .bp3-input[readonly], .bp3-control-group .bp3-input:disabled, .bp3-control-group .bp3-input.bp3-disabled{
      z-index:1; }
  .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input{
    z-index:13; }
    .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input:focus{
      z-index:15; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select select,
  .bp3-control-group .bp3-select select{
    -webkit-transform:translateZ(0);
            transform:translateZ(0);
    border-radius:inherit;
    z-index:4; }
    .bp3-control-group .bp3-button:focus,
    .bp3-control-group .bp3-html-select select:focus,
    .bp3-control-group .bp3-select select:focus{
      z-index:5; }
    .bp3-control-group .bp3-button:hover,
    .bp3-control-group .bp3-html-select select:hover,
    .bp3-control-group .bp3-select select:hover{
      z-index:6; }
    .bp3-control-group .bp3-button:active,
    .bp3-control-group .bp3-html-select select:active,
    .bp3-control-group .bp3-select select:active{
      z-index:7; }
    .bp3-control-group .bp3-button[readonly], .bp3-control-group .bp3-button:disabled, .bp3-control-group .bp3-button.bp3-disabled,
    .bp3-control-group .bp3-html-select select[readonly],
    .bp3-control-group .bp3-html-select select:disabled,
    .bp3-control-group .bp3-html-select select.bp3-disabled,
    .bp3-control-group .bp3-select select[readonly],
    .bp3-control-group .bp3-select select:disabled,
    .bp3-control-group .bp3-select select.bp3-disabled{
      z-index:3; }
    .bp3-control-group .bp3-button[class*="bp3-intent"],
    .bp3-control-group .bp3-html-select select[class*="bp3-intent"],
    .bp3-control-group .bp3-select select[class*="bp3-intent"]{
      z-index:9; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:focus{
        z-index:10; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:hover{
        z-index:11; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:active{
        z-index:12; }
      .bp3-control-group .bp3-button[class*="bp3-intent"][readonly], .bp3-control-group .bp3-button[class*="bp3-intent"]:disabled, .bp3-control-group .bp3-button[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"].bp3-disabled{
        z-index:8; }
  .bp3-control-group .bp3-input-group > .bp3-icon,
  .bp3-control-group .bp3-input-group > .bp3-button,
  .bp3-control-group .bp3-input-group > .bp3-input-left-container,
  .bp3-control-group .bp3-input-group > .bp3-input-action{
    z-index:16; }
  .bp3-control-group .bp3-select::after,
  .bp3-control-group .bp3-html-select::after,
  .bp3-control-group .bp3-select > .bp3-icon,
  .bp3-control-group .bp3-html-select > .bp3-icon{
    z-index:17; }
  .bp3-control-group .bp3-select:focus-within{
    z-index:5; }
  .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
    margin-right:-1px; }
  .bp3-control-group:not(.bp3-vertical) > .bp3-divider:not(:first-child){
    margin-left:6px; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
    margin-right:0; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > .bp3-button + .bp3-button{
    margin-left:1px; }
  .bp3-control-group .bp3-popover-wrapper,
  .bp3-control-group .bp3-popover-target{
    border-radius:inherit; }
  .bp3-control-group > :first-child{
    border-radius:3px 0 0 3px; }
  .bp3-control-group > :last-child{
    border-radius:0 3px 3px 0;
    margin-right:0; }
  .bp3-control-group > :only-child{
    border-radius:3px;
    margin-right:0; }
  .bp3-control-group .bp3-input-group .bp3-button{
    border-radius:3px; }
  .bp3-control-group .bp3-numeric-input:not(:first-child) .bp3-input-group{
    border-bottom-left-radius:0;
    border-top-left-radius:0; }
  .bp3-control-group.bp3-fill{
    width:100%; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-fill > *:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-vertical{
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column; }
    .bp3-control-group.bp3-vertical > *{
      margin-top:-1px; }
    .bp3-control-group.bp3-vertical > :first-child{
      border-radius:3px 3px 0 0;
      margin-top:0; }
    .bp3-control-group.bp3-vertical > :last-child{
      border-radius:0 0 3px 3px; }
.bp3-control{
  cursor:pointer;
  display:block;
  margin-bottom:10px;
  position:relative;
  text-transform:none; }
  .bp3-control input:checked ~ .bp3-control-indicator{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
  .bp3-control:hover input:checked ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
  .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    background:#0e5a8a;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-control input:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control:hover input:checked ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    background-color:#0e5a8a;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-control:not(.bp3-align-right){
    padding-left:26px; }
    .bp3-control:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-26px; }
  .bp3-control.bp3-align-right{
    padding-right:26px; }
    .bp3-control.bp3-align-right .bp3-control-indicator{
      margin-right:-26px; }
  .bp3-control.bp3-disabled{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-control.bp3-inline{
    display:inline-block;
    margin-right:20px; }
  .bp3-control input{
    left:0;
    opacity:0;
    position:absolute;
    top:0;
    z-index:-1; }
  .bp3-control .bp3-control-indicator{
    background-clip:padding-box;
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    border:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    cursor:pointer;
    display:inline-block;
    font-size:16px;
    height:1em;
    margin-right:10px;
    margin-top:-3px;
    position:relative;
    -webkit-user-select:none;
       -moz-user-select:none;
        -ms-user-select:none;
            user-select:none;
    vertical-align:middle;
    width:1em; }
    .bp3-control .bp3-control-indicator::before{
      content:"";
      display:block;
      height:1em;
      width:1em; }
  .bp3-control:hover .bp3-control-indicator{
    background-color:#ebf1f5; }
  .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
    background:#d8e1e8;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control input:disabled ~ .bp3-control-indicator{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    cursor:not-allowed; }
  .bp3-control input:focus ~ .bp3-control-indicator{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:2px;
    -moz-outline-radius:6px; }
  .bp3-control.bp3-align-right .bp3-control-indicator{
    float:right;
    margin-left:10px;
    margin-top:1px; }
  .bp3-control.bp3-large{
    font-size:16px; }
    .bp3-control.bp3-large:not(.bp3-align-right){
      padding-left:30px; }
      .bp3-control.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
        margin-left:-30px; }
    .bp3-control.bp3-large.bp3-align-right{
      padding-right:30px; }
      .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
        margin-right:-30px; }
    .bp3-control.bp3-large .bp3-control-indicator{
      font-size:20px; }
    .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-top:0; }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
  .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
  .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    background:#0e5a8a;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    background-color:#0e5a8a;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-control.bp3-checkbox .bp3-control-indicator{
    border-radius:3px; }
  .bp3-control.bp3-checkbox input:checked ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M12 5c-.28 0-.53.11-.71.29L7 9.59l-2.29-2.3a1.003 1.003 0 00-1.42 1.42l3 3c.18.18.43.29.71.29s.53-.11.71-.29l5-5A1.003 1.003 0 0012 5z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M11 7H5c-.55 0-1 .45-1 1s.45 1 1 1h6c.55 0 1-.45 1-1s-.45-1-1-1z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-radio .bp3-control-indicator{
    border-radius:50%; }
  .bp3-control.bp3-radio input:checked ~ .bp3-control-indicator::before{
    background-image:radial-gradient(#ffffff, #ffffff 28%, transparent 32%); }
  .bp3-control.bp3-radio input:checked:disabled ~ .bp3-control-indicator::before{
    opacity:0.5; }
  .bp3-control.bp3-radio input:focus ~ .bp3-control-indicator{
    -moz-outline-radius:16px; }
  .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(167, 182, 194, 0.5); }
  .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(115, 134, 148, 0.5); }
  .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(92, 112, 128, 0.5); }
  .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(206, 217, 224, 0.5); }
    .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5); }
    .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch:not(.bp3-align-right){
    padding-left:38px; }
    .bp3-control.bp3-switch:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-38px; }
  .bp3-control.bp3-switch.bp3-align-right{
    padding-right:38px; }
    .bp3-control.bp3-switch.bp3-align-right .bp3-control-indicator{
      margin-right:-38px; }
  .bp3-control.bp3-switch .bp3-control-indicator{
    border:none;
    border-radius:1.75em;
    -webkit-box-shadow:none !important;
            box-shadow:none !important;
    min-width:1.75em;
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    width:auto; }
    .bp3-control.bp3-switch .bp3-control-indicator::before{
      background:#ffffff;
      border-radius:50%;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
      height:calc(1em - 4px);
      left:0;
      margin:2px;
      position:absolute;
      -webkit-transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      width:calc(1em - 4px); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    left:calc(100% - 1em); }
  .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right){
    padding-left:45px; }
    .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-45px; }
  .bp3-control.bp3-switch.bp3-large.bp3-align-right{
    padding-right:45px; }
    .bp3-control.bp3-switch.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-right:-45px; }
  .bp3-dark .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.7); }
  .bp3-dark .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.9); }
  .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(57, 75, 89, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-dark .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-dark .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch .bp3-control-indicator::before{
    background:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-control.bp3-switch .bp3-switch-inner-text{
    font-size:0.7em;
    text-align:center; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:first-child{
    line-height:0;
    margin-left:0.5em;
    margin-right:1.2em;
    visibility:hidden; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:last-child{
    line-height:1em;
    margin-left:1.2em;
    margin-right:0.5em;
    visibility:visible; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:first-child{
    line-height:1em;
    visibility:visible; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:last-child{
    line-height:0;
    visibility:hidden; }
  .bp3-dark .bp3-control{
    color:#f5f8fa; }
    .bp3-dark .bp3-control.bp3-disabled{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-control .bp3-control-indicator{
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control:hover .bp3-control-indicator{
      background-color:#30404d; }
    .bp3-dark .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
      background:#202b33;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-control input:disabled ~ .bp3-control-indicator{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      cursor:not-allowed; }
    .bp3-dark .bp3-control.bp3-checkbox input:disabled:checked ~ .bp3-control-indicator, .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
      color:rgba(167, 182, 194, 0.6); }
.bp3-file-input{
  cursor:pointer;
  display:inline-block;
  height:30px;
  position:relative; }
  .bp3-file-input input{
    margin:0;
    min-width:200px;
    opacity:0; }
    .bp3-file-input input:disabled + .bp3-file-upload-input,
    .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
      background:rgba(206, 217, 224, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      resize:none; }
      .bp3-file-input input:disabled + .bp3-file-upload-input::after,
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
        background-color:rgba(206, 217, 224, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed;
        outline:none; }
        .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active:hover,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active:hover{
          background:rgba(206, 217, 224, 0.7); }
      .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input, .bp3-dark
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
        background:rgba(57, 75, 89, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after, .bp3-dark
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
          background-color:rgba(57, 75, 89, 0.5);
          background-image:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:rgba(167, 182, 194, 0.6); }
          .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-dark
          .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active{
            background:rgba(57, 75, 89, 0.7); }
  .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#182026; }
  .bp3-dark .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#f5f8fa; }
  .bp3-file-input.bp3-fill{
    width:100%; }
  .bp3-file-input.bp3-large,
  .bp3-large .bp3-file-input{
    height:40px; }
  .bp3-file-input .bp3-file-upload-input-custom-text::after{
    content:attr(bp3-button-text); }

.bp3-file-upload-input{
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none;
  background:#ffffff;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#182026;
  font-size:14px;
  font-weight:400;
  height:30px;
  line-height:30px;
  outline:none;
  padding:0 10px;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  vertical-align:middle;
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  color:rgba(92, 112, 128, 0.6);
  left:0;
  padding-right:80px;
  position:absolute;
  right:0;
  top:0;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-file-upload-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input:focus, .bp3-file-upload-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-file-upload-input[type="search"], .bp3-file-upload-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-file-upload-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-file-upload-input:disabled, .bp3-file-upload-input.bp3-disabled{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    resize:none; }
  .bp3-file-upload-input::after{
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026;
    min-height:24px;
    min-width:24px;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    border-radius:3px;
    content:"Browse";
    line-height:24px;
    margin:3px;
    position:absolute;
    right:0;
    text-align:center;
    top:0;
    width:70px; }
    .bp3-file-upload-input::after:hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-file-upload-input::after:active, .bp3-file-upload-input::after.bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-file-upload-input::after:disabled, .bp3-file-upload-input::after.bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-file-upload-input::after:disabled.bp3-active, .bp3-file-upload-input::after:disabled.bp3-active:hover, .bp3-file-upload-input::after.bp3-disabled.bp3-active, .bp3-file-upload-input::after.bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-file-upload-input:hover::after{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-file-upload-input:active::after{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-large .bp3-file-upload-input{
    font-size:16px;
    height:40px;
    line-height:40px;
    padding-right:95px; }
    .bp3-large .bp3-file-upload-input[type="search"], .bp3-large .bp3-file-upload-input.bp3-round{
      padding:0 15px; }
    .bp3-large .bp3-file-upload-input::after{
      min-height:30px;
      min-width:30px;
      line-height:30px;
      margin:5px;
      width:85px; }
  .bp3-dark .bp3-file-upload-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input:disabled, .bp3-dark .bp3-file-upload-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::after{
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover, .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover{
        background-color:#30404d;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        background-color:#202b33;
        background-image:none;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-dark .bp3-file-upload-input::after:disabled, .bp3-dark .bp3-file-upload-input::after.bp3-disabled{
        background-color:rgba(57, 75, 89, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-upload-input::after:disabled.bp3-active, .bp3-dark .bp3-file-upload-input::after.bp3-disabled.bp3-active{
          background:rgba(57, 75, 89, 0.7); }
      .bp3-dark .bp3-file-upload-input::after .bp3-button-spinner .bp3-spinner-head{
        background:rgba(16, 22, 26, 0.5);
        stroke:#8a9ba8; }
    .bp3-dark .bp3-file-upload-input:hover::after{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input:active::after{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
.bp3-file-upload-input::after{
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
.bp3-form-group{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0 0 15px; }
  .bp3-form-group label.bp3-label{
    margin-bottom:5px; }
  .bp3-form-group .bp3-control{
    margin-top:7px; }
  .bp3-form-group .bp3-form-helper-text{
    color:#5c7080;
    font-size:12px;
    margin-top:5px; }
  .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#106ba3; }
  .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#0d8050; }
  .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#bf7326; }
  .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#c23030; }
  .bp3-form-group.bp3-inline{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row; }
    .bp3-form-group.bp3-inline.bp3-large label.bp3-label{
      line-height:40px;
      margin:0 10px 0 0; }
    .bp3-form-group.bp3-inline label.bp3-label{
      line-height:30px;
      margin:0 10px 0 0; }
  .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-dark .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#48aff0; }
  .bp3-dark .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#3dcc91; }
  .bp3-dark .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#ffb366; }
  .bp3-dark .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#ff7373; }
  .bp3-dark .bp3-form-group .bp3-form-helper-text{
    color:#a7b6c2; }
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(167, 182, 194, 0.6) !important; }
.bp3-input-group{
  display:block;
  position:relative; }
  .bp3-input-group .bp3-input{
    position:relative;
    width:100%; }
    .bp3-input-group .bp3-input:not(:first-child){
      padding-left:30px; }
    .bp3-input-group .bp3-input:not(:last-child){
      padding-right:30px; }
  .bp3-input-group .bp3-input-action,
  .bp3-input-group > .bp3-input-left-container,
  .bp3-input-group > .bp3-button,
  .bp3-input-group > .bp3-icon{
    position:absolute;
    top:0; }
    .bp3-input-group .bp3-input-action:first-child,
    .bp3-input-group > .bp3-input-left-container:first-child,
    .bp3-input-group > .bp3-button:first-child,
    .bp3-input-group > .bp3-icon:first-child{
      left:0; }
    .bp3-input-group .bp3-input-action:last-child,
    .bp3-input-group > .bp3-input-left-container:last-child,
    .bp3-input-group > .bp3-button:last-child,
    .bp3-input-group > .bp3-icon:last-child{
      right:0; }
  .bp3-input-group .bp3-button{
    min-height:24px;
    min-width:24px;
    margin:3px;
    padding:0 7px; }
    .bp3-input-group .bp3-button:empty{
      padding:0; }
  .bp3-input-group > .bp3-input-left-container,
  .bp3-input-group > .bp3-icon{
    z-index:1; }
  .bp3-input-group > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group > .bp3-icon{
    color:#5c7080; }
    .bp3-input-group > .bp3-input-left-container > .bp3-icon:empty,
    .bp3-input-group > .bp3-icon:empty{
      font-family:"Icons16", sans-serif;
      font-size:16px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased; }
  .bp3-input-group > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group > .bp3-icon,
  .bp3-input-group .bp3-input-action > .bp3-spinner{
    margin:7px; }
  .bp3-input-group .bp3-tag{
    margin:5px; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus),
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
    color:#5c7080; }
    .bp3-dark .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus), .bp3-dark
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
      color:#a7b6c2; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large{
      color:#5c7080; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled,
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled{
    color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-large{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-input-group.bp3-disabled{
    cursor:not-allowed; }
    .bp3-input-group.bp3-disabled .bp3-icon{
      color:rgba(92, 112, 128, 0.6); }
  .bp3-input-group.bp3-large .bp3-button{
    min-height:30px;
    min-width:30px;
    margin:5px; }
  .bp3-input-group.bp3-large > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group.bp3-large > .bp3-icon,
  .bp3-input-group.bp3-large .bp3-input-action > .bp3-spinner{
    margin:12px; }
  .bp3-input-group.bp3-large .bp3-input{
    font-size:16px;
    height:40px;
    line-height:40px; }
    .bp3-input-group.bp3-large .bp3-input[type="search"], .bp3-input-group.bp3-large .bp3-input.bp3-round{
      padding:0 15px; }
    .bp3-input-group.bp3-large .bp3-input:not(:first-child){
      padding-left:40px; }
    .bp3-input-group.bp3-large .bp3-input:not(:last-child){
      padding-right:40px; }
  .bp3-input-group.bp3-small .bp3-button{
    min-height:20px;
    min-width:20px;
    margin:2px; }
  .bp3-input-group.bp3-small .bp3-tag{
    min-height:20px;
    min-width:20px;
    margin:2px; }
  .bp3-input-group.bp3-small > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group.bp3-small > .bp3-icon,
  .bp3-input-group.bp3-small .bp3-input-action > .bp3-spinner{
    margin:4px; }
  .bp3-input-group.bp3-small .bp3-input{
    font-size:12px;
    height:24px;
    line-height:24px;
    padding-left:8px;
    padding-right:8px; }
    .bp3-input-group.bp3-small .bp3-input[type="search"], .bp3-input-group.bp3-small .bp3-input.bp3-round{
      padding:0 12px; }
    .bp3-input-group.bp3-small .bp3-input:not(:first-child){
      padding-left:24px; }
    .bp3-input-group.bp3-small .bp3-input:not(:last-child){
      padding-right:24px; }
  .bp3-input-group.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-input-group.bp3-round .bp3-button,
  .bp3-input-group.bp3-round .bp3-input,
  .bp3-input-group.bp3-round .bp3-tag{
    border-radius:30px; }
  .bp3-dark .bp3-input-group .bp3-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-input-group.bp3-disabled .bp3-icon{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-input-group.bp3-intent-primary .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input-group.bp3-intent-primary .bp3-input:disabled, .bp3-input-group.bp3-intent-primary .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-primary > .bp3-icon{
    color:#106ba3; }
    .bp3-dark .bp3-input-group.bp3-intent-primary > .bp3-icon{
      color:#48aff0; }
  .bp3-input-group.bp3-intent-success .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input-group.bp3-intent-success .bp3-input:disabled, .bp3-input-group.bp3-intent-success .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-success > .bp3-icon{
    color:#0d8050; }
    .bp3-dark .bp3-input-group.bp3-intent-success > .bp3-icon{
      color:#3dcc91; }
  .bp3-input-group.bp3-intent-warning .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input-group.bp3-intent-warning .bp3-input:disabled, .bp3-input-group.bp3-intent-warning .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-warning > .bp3-icon{
    color:#bf7326; }
    .bp3-dark .bp3-input-group.bp3-intent-warning > .bp3-icon{
      color:#ffb366; }
  .bp3-input-group.bp3-intent-danger .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input-group.bp3-intent-danger .bp3-input:disabled, .bp3-input-group.bp3-intent-danger .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-danger > .bp3-icon{
    color:#c23030; }
    .bp3-dark .bp3-input-group.bp3-intent-danger > .bp3-icon{
      color:#ff7373; }
.bp3-input{
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none;
  background:#ffffff;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#182026;
  font-size:14px;
  font-weight:400;
  height:30px;
  line-height:30px;
  outline:none;
  padding:0 10px;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  vertical-align:middle; }
  .bp3-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input:focus, .bp3-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-input[type="search"], .bp3-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-input:disabled, .bp3-input.bp3-disabled{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    resize:none; }
  .bp3-input.bp3-large{
    font-size:16px;
    height:40px;
    line-height:40px; }
    .bp3-input.bp3-large[type="search"], .bp3-input.bp3-large.bp3-round{
      padding:0 15px; }
  .bp3-input.bp3-small{
    font-size:12px;
    height:24px;
    line-height:24px;
    padding-left:8px;
    padding-right:8px; }
    .bp3-input.bp3-small[type="search"], .bp3-input.bp3-small.bp3-round{
      padding:0 12px; }
  .bp3-input.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-dark .bp3-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input:disabled, .bp3-dark .bp3-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
  .bp3-input.bp3-intent-primary{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input.bp3-intent-primary:disabled, .bp3-input.bp3-intent-primary.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #137cbd;
                box-shadow:inset 0 0 0 1px #137cbd; }
      .bp3-dark .bp3-input.bp3-intent-primary:disabled, .bp3-dark .bp3-input.bp3-intent-primary.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-success{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input.bp3-intent-success:disabled, .bp3-input.bp3-intent-success.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-success{
      -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success:focus{
        -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #0f9960;
                box-shadow:inset 0 0 0 1px #0f9960; }
      .bp3-dark .bp3-input.bp3-intent-success:disabled, .bp3-dark .bp3-input.bp3-intent-success.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-warning{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input.bp3-intent-warning:disabled, .bp3-input.bp3-intent-warning.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning:focus{
        -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #d9822b;
                box-shadow:inset 0 0 0 1px #d9822b; }
      .bp3-dark .bp3-input.bp3-intent-warning:disabled, .bp3-dark .bp3-input.bp3-intent-warning.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-danger{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input.bp3-intent-danger:disabled, .bp3-input.bp3-intent-danger.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger:focus{
        -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #db3737;
                box-shadow:inset 0 0 0 1px #db3737; }
      .bp3-dark .bp3-input.bp3-intent-danger:disabled, .bp3-dark .bp3-input.bp3-intent-danger.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input::-ms-clear{
    display:none; }
textarea.bp3-input{
  max-width:100%;
  padding:10px; }
  textarea.bp3-input, textarea.bp3-input.bp3-large, textarea.bp3-input.bp3-small{
    height:auto;
    line-height:inherit; }
  textarea.bp3-input.bp3-small{
    padding:8px; }
  .bp3-dark textarea.bp3-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark textarea.bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input:disabled, .bp3-dark textarea.bp3-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
label.bp3-label{
  display:block;
  margin-bottom:15px;
  margin-top:0; }
  label.bp3-label .bp3-html-select,
  label.bp3-label .bp3-input,
  label.bp3-label .bp3-select,
  label.bp3-label .bp3-slider,
  label.bp3-label .bp3-popover-wrapper{
    display:block;
    margin-top:5px;
    text-transform:none; }
  label.bp3-label .bp3-button-group{
    margin-top:5px; }
  label.bp3-label .bp3-select select,
  label.bp3-label .bp3-html-select select{
    font-weight:400;
    vertical-align:top;
    width:100%; }
  label.bp3-label.bp3-disabled,
  label.bp3-label.bp3-disabled .bp3-text-muted{
    color:rgba(92, 112, 128, 0.6); }
  label.bp3-label.bp3-inline{
    line-height:30px; }
    label.bp3-label.bp3-inline .bp3-html-select,
    label.bp3-label.bp3-inline .bp3-input,
    label.bp3-label.bp3-inline .bp3-input-group,
    label.bp3-label.bp3-inline .bp3-select,
    label.bp3-label.bp3-inline .bp3-popover-wrapper{
      display:inline-block;
      margin:0 0 0 5px;
      vertical-align:top; }
    label.bp3-label.bp3-inline .bp3-button-group{
      margin:0 0 0 5px; }
    label.bp3-label.bp3-inline .bp3-input-group .bp3-input{
      margin-left:0; }
    label.bp3-label.bp3-inline.bp3-large{
      line-height:40px; }
  label.bp3-label:not(.bp3-inline) .bp3-popover-target{
    display:block; }
  .bp3-dark label.bp3-label{
    color:#f5f8fa; }
    .bp3-dark label.bp3-label.bp3-disabled,
    .bp3-dark label.bp3-label.bp3-disabled .bp3-text-muted{
      color:rgba(167, 182, 194, 0.6); }
.bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button{
  -webkit-box-flex:1;
      -ms-flex:1 1 14px;
          flex:1 1 14px;
  min-height:0;
  padding:0;
  width:30px; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:first-child{
    border-radius:0 3px 0 0; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:last-child{
    border-radius:0 0 3px 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:first-child{
  border-radius:3px 0 0 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:last-child{
  border-radius:0 0 0 3px; }

.bp3-numeric-input.bp3-large .bp3-button-group.bp3-vertical > .bp3-button{
  width:40px; }

form{
  display:block; }
.bp3-html-select select,
.bp3-select select{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  font-size:14px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  padding:5px 10px;
  text-align:left;
  vertical-align:middle;
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  color:#182026;
  -moz-appearance:none;
  -webkit-appearance:none;
  border-radius:3px;
  height:30px;
  padding:0 25px 0 10px;
  width:100%; }
  .bp3-html-select select > *, .bp3-select select > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-html-select select > .bp3-fill, .bp3-select select > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-html-select select::before,
  .bp3-select select::before, .bp3-html-select select > *, .bp3-select select > *{
    margin-right:7px; }
  .bp3-html-select select:empty::before,
  .bp3-select select:empty::before,
  .bp3-html-select select > :last-child,
  .bp3-select select > :last-child{
    margin-right:0; }
  .bp3-html-select select:hover,
  .bp3-select select:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-html-select select:active,
  .bp3-select select:active, .bp3-html-select select.bp3-active,
  .bp3-select select.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-html-select select:disabled,
  .bp3-select select:disabled, .bp3-html-select select.bp3-disabled,
  .bp3-select select.bp3-disabled{
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    outline:none; }
    .bp3-html-select select:disabled.bp3-active,
    .bp3-select select:disabled.bp3-active, .bp3-html-select select:disabled.bp3-active:hover,
    .bp3-select select:disabled.bp3-active:hover, .bp3-html-select select.bp3-disabled.bp3-active,
    .bp3-select select.bp3-disabled.bp3-active, .bp3-html-select select.bp3-disabled.bp3-active:hover,
    .bp3-select select.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }

.bp3-html-select.bp3-minimal select,
.bp3-select.bp3-minimal select{
  background:none;
  -webkit-box-shadow:none;
          box-shadow:none; }
  .bp3-html-select.bp3-minimal select:hover,
  .bp3-select.bp3-minimal select:hover{
    background:rgba(167, 182, 194, 0.3);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:#182026;
    text-decoration:none; }
  .bp3-html-select.bp3-minimal select:active,
  .bp3-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal select.bp3-active,
  .bp3-select.bp3-minimal select.bp3-active{
    background:rgba(115, 134, 148, 0.3);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:#182026; }
  .bp3-html-select.bp3-minimal select:disabled,
  .bp3-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal select:disabled:hover,
  .bp3-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal select.bp3-disabled,
  .bp3-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal select.bp3-disabled:hover,
  .bp3-select.bp3-minimal select.bp3-disabled:hover{
    background:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
    .bp3-html-select.bp3-minimal select:disabled.bp3-active,
    .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active{
      background:rgba(115, 134, 148, 0.3); }
  .bp3-dark .bp3-html-select.bp3-minimal select, .bp3-html-select.bp3-minimal .bp3-dark select,
  .bp3-dark .bp3-select.bp3-minimal select, .bp3-select.bp3-minimal .bp3-dark select{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:inherit; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover, .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover{
      background:rgba(138, 155, 168, 0.15); }
    .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      background:rgba(138, 155, 168, 0.3);
      color:#f5f8fa; }
    .bp3-dark .bp3-html-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal .bp3-dark select:disabled,
    .bp3-dark .bp3-select.bp3-minimal select:disabled, .bp3-select.bp3-minimal .bp3-dark select:disabled, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select:disabled:hover, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover{
      background:none;
      color:rgba(167, 182, 194, 0.6);
      cursor:not-allowed; }
      .bp3-dark .bp3-html-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active{
        background:rgba(138, 155, 168, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-primary,
  .bp3-select.bp3-minimal select.bp3-intent-primary{
    color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover{
      background:rgba(19, 124, 189, 0.15);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      background:rgba(19, 124, 189, 0.3);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled{
      background:none;
      color:rgba(16, 107, 163, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active{
        background:rgba(19, 124, 189, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
      stroke:#106ba3; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary{
      color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.2);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(72, 175, 240, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-success,
  .bp3-select.bp3-minimal select.bp3-intent-success{
    color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover{
      background:rgba(15, 153, 96, 0.15);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      background:rgba(15, 153, 96, 0.3);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled{
      background:none;
      color:rgba(13, 128, 80, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active{
        background:rgba(15, 153, 96, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
      stroke:#0d8050; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success{
      color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.2);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(61, 204, 145, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-warning,
  .bp3-select.bp3-minimal select.bp3-intent-warning{
    color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover{
      background:rgba(217, 130, 43, 0.15);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      background:rgba(217, 130, 43, 0.3);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled{
      background:none;
      color:rgba(191, 115, 38, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active{
        background:rgba(217, 130, 43, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
      stroke:#bf7326; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning{
      color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.2);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(255, 179, 102, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-danger,
  .bp3-select.bp3-minimal select.bp3-intent-danger{
    color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover{
      background:rgba(219, 55, 55, 0.15);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      background:rgba(219, 55, 55, 0.3);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled{
      background:none;
      color:rgba(194, 48, 48, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active{
        background:rgba(219, 55, 55, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
      stroke:#c23030; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger{
      color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.2);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(255, 115, 115, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }

.bp3-html-select.bp3-large select,
.bp3-select.bp3-large select{
  font-size:16px;
  height:40px;
  padding-right:35px; }

.bp3-dark .bp3-html-select select, .bp3-dark .bp3-select select{
  background-color:#394b59;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
  color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover, .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    background-color:#202b33;
    background-image:none;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-html-select select:disabled, .bp3-dark .bp3-select select:disabled, .bp3-dark .bp3-html-select select.bp3-disabled, .bp3-dark .bp3-select select.bp3-disabled{
    background-color:rgba(57, 75, 89, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-html-select select:disabled.bp3-active, .bp3-dark .bp3-select select:disabled.bp3-active, .bp3-dark .bp3-html-select select.bp3-disabled.bp3-active, .bp3-dark .bp3-select select.bp3-disabled.bp3-active{
      background:rgba(57, 75, 89, 0.7); }
  .bp3-dark .bp3-html-select select .bp3-button-spinner .bp3-spinner-head, .bp3-dark .bp3-select select .bp3-button-spinner .bp3-spinner-head{
    background:rgba(16, 22, 26, 0.5);
    stroke:#8a9ba8; }

.bp3-html-select select:disabled,
.bp3-select select:disabled{
  background-color:rgba(206, 217, 224, 0.5);
  -webkit-box-shadow:none;
          box-shadow:none;
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-html-select .bp3-icon,
.bp3-select .bp3-icon, .bp3-select::after{
  color:#5c7080;
  pointer-events:none;
  position:absolute;
  right:7px;
  top:7px; }
  .bp3-html-select .bp3-disabled.bp3-icon,
  .bp3-select .bp3-disabled.bp3-icon, .bp3-disabled.bp3-select::after{
    color:rgba(92, 112, 128, 0.6); }
.bp3-html-select,
.bp3-select{
  display:inline-block;
  letter-spacing:normal;
  position:relative;
  vertical-align:middle; }
  .bp3-html-select select::-ms-expand,
  .bp3-select select::-ms-expand{
    display:none; }
  .bp3-html-select .bp3-icon,
  .bp3-select .bp3-icon{
    color:#5c7080; }
    .bp3-html-select .bp3-icon:hover,
    .bp3-select .bp3-icon:hover{
      color:#182026; }
    .bp3-dark .bp3-html-select .bp3-icon, .bp3-dark
    .bp3-select .bp3-icon{
      color:#a7b6c2; }
      .bp3-dark .bp3-html-select .bp3-icon:hover, .bp3-dark
      .bp3-select .bp3-icon:hover{
        color:#f5f8fa; }
  .bp3-html-select.bp3-large::after,
  .bp3-html-select.bp3-large .bp3-icon,
  .bp3-select.bp3-large::after,
  .bp3-select.bp3-large .bp3-icon{
    right:12px;
    top:12px; }
  .bp3-html-select.bp3-fill,
  .bp3-html-select.bp3-fill select,
  .bp3-select.bp3-fill,
  .bp3-select.bp3-fill select{
    width:100%; }
  .bp3-dark .bp3-html-select option, .bp3-dark
  .bp3-select option{
    background-color:#30404d;
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select option:disabled, .bp3-dark
  .bp3-select option:disabled{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-html-select::after, .bp3-dark
  .bp3-select::after{
    color:#a7b6c2; }

.bp3-select::after{
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  content:""; }
.bp3-running-text table, table.bp3-html-table{
  border-spacing:0;
  font-size:14px; }
  .bp3-running-text table th, table.bp3-html-table th,
  .bp3-running-text table td,
  table.bp3-html-table td{
    padding:11px;
    text-align:left;
    vertical-align:top; }
  .bp3-running-text table th, table.bp3-html-table th{
    color:#182026;
    font-weight:600; }
  
  .bp3-running-text table td,
  table.bp3-html-table td{
    color:#182026; }
  .bp3-running-text table tbody tr:first-child th, table.bp3-html-table tbody tr:first-child th,
  .bp3-running-text table tbody tr:first-child td,
  table.bp3-html-table tbody tr:first-child td,
  .bp3-running-text table tfoot tr:first-child th,
  table.bp3-html-table tfoot tr:first-child th,
  .bp3-running-text table tfoot tr:first-child td,
  table.bp3-html-table tfoot tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-running-text table th, .bp3-running-text .bp3-dark table th, .bp3-dark table.bp3-html-table th{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table td, .bp3-running-text .bp3-dark table td, .bp3-dark table.bp3-html-table td{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table tbody tr:first-child th, .bp3-running-text .bp3-dark table tbody tr:first-child th, .bp3-dark table.bp3-html-table tbody tr:first-child th,
  .bp3-dark .bp3-running-text table tbody tr:first-child td,
  .bp3-running-text .bp3-dark table tbody tr:first-child td,
  .bp3-dark table.bp3-html-table tbody tr:first-child td,
  .bp3-dark .bp3-running-text table tfoot tr:first-child th,
  .bp3-running-text .bp3-dark table tfoot tr:first-child th,
  .bp3-dark table.bp3-html-table tfoot tr:first-child th,
  .bp3-dark .bp3-running-text table tfoot tr:first-child td,
  .bp3-running-text .bp3-dark table tfoot tr:first-child td,
  .bp3-dark table.bp3-html-table tfoot tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }

table.bp3-html-table.bp3-html-table-condensed th,
table.bp3-html-table.bp3-html-table-condensed td, table.bp3-html-table.bp3-small th,
table.bp3-html-table.bp3-small td{
  padding-bottom:6px;
  padding-top:6px; }

table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
  background:rgba(191, 204, 214, 0.15); }

table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
  -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered tbody tr td,
table.bp3-html-table.bp3-html-table-bordered tfoot tr td{
  -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child),
  table.bp3-html-table.bp3-html-table-bordered tfoot tr td:not(:first-child){
    -webkit-box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
  -webkit-box-shadow:none;
          box-shadow:none; }
  table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-interactive tbody tr:hover td{
  background-color:rgba(191, 204, 214, 0.3);
  cursor:pointer; }

table.bp3-html-table.bp3-interactive tbody tr:active td{
  background-color:rgba(191, 204, 214, 0.4); }

.bp3-dark table.bp3-html-table{ }
  .bp3-dark table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
    background:rgba(92, 112, 128, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td,
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered tfoot tr td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child),
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered tfoot tr td:not(:first-child){
      -webkit-box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15);
              box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
    -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:first-child{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:hover td{
    background-color:rgba(92, 112, 128, 0.3);
    cursor:pointer; }
  .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:active td{
    background-color:rgba(92, 112, 128, 0.4); }

.bp3-key-combo{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center; }
  .bp3-key-combo > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-key-combo > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-key-combo::before,
  .bp3-key-combo > *{
    margin-right:5px; }
  .bp3-key-combo:empty::before,
  .bp3-key-combo > :last-child{
    margin-right:0; }

.bp3-hotkey-dialog{
  padding-bottom:0;
  top:40px; }
  .bp3-hotkey-dialog .bp3-dialog-body{
    margin:0;
    padding:0; }
  .bp3-hotkey-dialog .bp3-hotkey-label{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1; }

.bp3-hotkey-column{
  margin:auto;
  max-height:80vh;
  overflow-y:auto;
  padding:30px; }
  .bp3-hotkey-column .bp3-heading{
    margin-bottom:20px; }
    .bp3-hotkey-column .bp3-heading:not(:first-child){
      margin-top:40px; }

.bp3-hotkey{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:justify;
      -ms-flex-pack:justify;
          justify-content:space-between;
  margin-left:0;
  margin-right:0; }
  .bp3-hotkey:not(:last-child){
    margin-bottom:10px; }
.bp3-icon{
  display:inline-block;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  vertical-align:text-bottom; }
  .bp3-icon:not(:empty)::before{
    content:"" !important;
    content:unset !important; }
  .bp3-icon > svg{
    display:block; }
    .bp3-icon > svg:not([fill]){
      fill:currentColor; }

.bp3-icon.bp3-intent-primary, .bp3-icon-standard.bp3-intent-primary, .bp3-icon-large.bp3-intent-primary{
  color:#106ba3; }
  .bp3-dark .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-icon-large.bp3-intent-primary{
    color:#48aff0; }

.bp3-icon.bp3-intent-success, .bp3-icon-standard.bp3-intent-success, .bp3-icon-large.bp3-intent-success{
  color:#0d8050; }
  .bp3-dark .bp3-icon.bp3-intent-success, .bp3-dark .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-icon-large.bp3-intent-success{
    color:#3dcc91; }

.bp3-icon.bp3-intent-warning, .bp3-icon-standard.bp3-intent-warning, .bp3-icon-large.bp3-intent-warning{
  color:#bf7326; }
  .bp3-dark .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-icon-large.bp3-intent-warning{
    color:#ffb366; }

.bp3-icon.bp3-intent-danger, .bp3-icon-standard.bp3-intent-danger, .bp3-icon-large.bp3-intent-danger{
  color:#c23030; }
  .bp3-dark .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-icon-large.bp3-intent-danger{
    color:#ff7373; }

span.bp3-icon-standard{
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon-large{
  font-family:"Icons20", sans-serif;
  font-size:20px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon:empty{
  font-family:"Icons20";
  font-size:inherit;
  font-style:normal;
  font-weight:400;
  line-height:1; }
  span.bp3-icon:empty::before{
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased; }

.bp3-icon-add::before{
  content:""; }

.bp3-icon-add-column-left::before{
  content:""; }

.bp3-icon-add-column-right::before{
  content:""; }

.bp3-icon-add-row-bottom::before{
  content:""; }

.bp3-icon-add-row-top::before{
  content:""; }

.bp3-icon-add-to-artifact::before{
  content:""; }

.bp3-icon-add-to-folder::before{
  content:""; }

.bp3-icon-airplane::before{
  content:""; }

.bp3-icon-align-center::before{
  content:""; }

.bp3-icon-align-justify::before{
  content:""; }

.bp3-icon-align-left::before{
  content:""; }

.bp3-icon-align-right::before{
  content:""; }

.bp3-icon-alignment-bottom::before{
  content:""; }

.bp3-icon-alignment-horizontal-center::before{
  content:""; }

.bp3-icon-alignment-left::before{
  content:""; }

.bp3-icon-alignment-right::before{
  content:""; }

.bp3-icon-alignment-top::before{
  content:""; }

.bp3-icon-alignment-vertical-center::before{
  content:""; }

.bp3-icon-annotation::before{
  content:""; }

.bp3-icon-application::before{
  content:""; }

.bp3-icon-applications::before{
  content:""; }

.bp3-icon-archive::before{
  content:""; }

.bp3-icon-arrow-bottom-left::before{
  content:"↙"; }

.bp3-icon-arrow-bottom-right::before{
  content:"↘"; }

.bp3-icon-arrow-down::before{
  content:"↓"; }

.bp3-icon-arrow-left::before{
  content:"←"; }

.bp3-icon-arrow-right::before{
  content:"→"; }

.bp3-icon-arrow-top-left::before{
  content:"↖"; }

.bp3-icon-arrow-top-right::before{
  content:"↗"; }

.bp3-icon-arrow-up::before{
  content:"↑"; }

.bp3-icon-arrows-horizontal::before{
  content:"↔"; }

.bp3-icon-arrows-vertical::before{
  content:"↕"; }

.bp3-icon-asterisk::before{
  content:"*"; }

.bp3-icon-automatic-updates::before{
  content:""; }

.bp3-icon-badge::before{
  content:""; }

.bp3-icon-ban-circle::before{
  content:""; }

.bp3-icon-bank-account::before{
  content:""; }

.bp3-icon-barcode::before{
  content:""; }

.bp3-icon-blank::before{
  content:""; }

.bp3-icon-blocked-person::before{
  content:""; }

.bp3-icon-bold::before{
  content:""; }

.bp3-icon-book::before{
  content:""; }

.bp3-icon-bookmark::before{
  content:""; }

.bp3-icon-box::before{
  content:""; }

.bp3-icon-briefcase::before{
  content:""; }

.bp3-icon-bring-data::before{
  content:""; }

.bp3-icon-build::before{
  content:""; }

.bp3-icon-calculator::before{
  content:""; }

.bp3-icon-calendar::before{
  content:""; }

.bp3-icon-camera::before{
  content:""; }

.bp3-icon-caret-down::before{
  content:"⌄"; }

.bp3-icon-caret-left::before{
  content:"〈"; }

.bp3-icon-caret-right::before{
  content:"〉"; }

.bp3-icon-caret-up::before{
  content:"⌃"; }

.bp3-icon-cell-tower::before{
  content:""; }

.bp3-icon-changes::before{
  content:""; }

.bp3-icon-chart::before{
  content:""; }

.bp3-icon-chat::before{
  content:""; }

.bp3-icon-chevron-backward::before{
  content:""; }

.bp3-icon-chevron-down::before{
  content:""; }

.bp3-icon-chevron-forward::before{
  content:""; }

.bp3-icon-chevron-left::before{
  content:""; }

.bp3-icon-chevron-right::before{
  content:""; }

.bp3-icon-chevron-up::before{
  content:""; }

.bp3-icon-circle::before{
  content:""; }

.bp3-icon-circle-arrow-down::before{
  content:""; }

.bp3-icon-circle-arrow-left::before{
  content:""; }

.bp3-icon-circle-arrow-right::before{
  content:""; }

.bp3-icon-circle-arrow-up::before{
  content:""; }

.bp3-icon-citation::before{
  content:""; }

.bp3-icon-clean::before{
  content:""; }

.bp3-icon-clipboard::before{
  content:""; }

.bp3-icon-cloud::before{
  content:"☁"; }

.bp3-icon-cloud-download::before{
  content:""; }

.bp3-icon-cloud-upload::before{
  content:""; }

.bp3-icon-code::before{
  content:""; }

.bp3-icon-code-block::before{
  content:""; }

.bp3-icon-cog::before{
  content:""; }

.bp3-icon-collapse-all::before{
  content:""; }

.bp3-icon-column-layout::before{
  content:""; }

.bp3-icon-comment::before{
  content:""; }

.bp3-icon-comparison::before{
  content:""; }

.bp3-icon-compass::before{
  content:""; }

.bp3-icon-compressed::before{
  content:""; }

.bp3-icon-confirm::before{
  content:""; }

.bp3-icon-console::before{
  content:""; }

.bp3-icon-contrast::before{
  content:""; }

.bp3-icon-control::before{
  content:""; }

.bp3-icon-credit-card::before{
  content:""; }

.bp3-icon-cross::before{
  content:"✗"; }

.bp3-icon-crown::before{
  content:""; }

.bp3-icon-cube::before{
  content:""; }

.bp3-icon-cube-add::before{
  content:""; }

.bp3-icon-cube-remove::before{
  content:""; }

.bp3-icon-curved-range-chart::before{
  content:""; }

.bp3-icon-cut::before{
  content:""; }

.bp3-icon-dashboard::before{
  content:""; }

.bp3-icon-data-lineage::before{
  content:""; }

.bp3-icon-database::before{
  content:""; }

.bp3-icon-delete::before{
  content:""; }

.bp3-icon-delta::before{
  content:"Δ"; }

.bp3-icon-derive-column::before{
  content:""; }

.bp3-icon-desktop::before{
  content:""; }

.bp3-icon-diagnosis::before{
  content:""; }

.bp3-icon-diagram-tree::before{
  content:""; }

.bp3-icon-direction-left::before{
  content:""; }

.bp3-icon-direction-right::before{
  content:""; }

.bp3-icon-disable::before{
  content:""; }

.bp3-icon-document::before{
  content:""; }

.bp3-icon-document-open::before{
  content:""; }

.bp3-icon-document-share::before{
  content:""; }

.bp3-icon-dollar::before{
  content:"$"; }

.bp3-icon-dot::before{
  content:"•"; }

.bp3-icon-double-caret-horizontal::before{
  content:""; }

.bp3-icon-double-caret-vertical::before{
  content:""; }

.bp3-icon-double-chevron-down::before{
  content:""; }

.bp3-icon-double-chevron-left::before{
  content:""; }

.bp3-icon-double-chevron-right::before{
  content:""; }

.bp3-icon-double-chevron-up::before{
  content:""; }

.bp3-icon-doughnut-chart::before{
  content:""; }

.bp3-icon-download::before{
  content:""; }

.bp3-icon-drag-handle-horizontal::before{
  content:""; }

.bp3-icon-drag-handle-vertical::before{
  content:""; }

.bp3-icon-draw::before{
  content:""; }

.bp3-icon-drive-time::before{
  content:""; }

.bp3-icon-duplicate::before{
  content:""; }

.bp3-icon-edit::before{
  content:"✎"; }

.bp3-icon-eject::before{
  content:"⏏"; }

.bp3-icon-endorsed::before{
  content:""; }

.bp3-icon-envelope::before{
  content:"✉"; }

.bp3-icon-equals::before{
  content:""; }

.bp3-icon-eraser::before{
  content:""; }

.bp3-icon-error::before{
  content:""; }

.bp3-icon-euro::before{
  content:"€"; }

.bp3-icon-exchange::before{
  content:""; }

.bp3-icon-exclude-row::before{
  content:""; }

.bp3-icon-expand-all::before{
  content:""; }

.bp3-icon-export::before{
  content:""; }

.bp3-icon-eye-off::before{
  content:""; }

.bp3-icon-eye-on::before{
  content:""; }

.bp3-icon-eye-open::before{
  content:""; }

.bp3-icon-fast-backward::before{
  content:""; }

.bp3-icon-fast-forward::before{
  content:""; }

.bp3-icon-feed::before{
  content:""; }

.bp3-icon-feed-subscribed::before{
  content:""; }

.bp3-icon-film::before{
  content:""; }

.bp3-icon-filter::before{
  content:""; }

.bp3-icon-filter-keep::before{
  content:""; }

.bp3-icon-filter-list::before{
  content:""; }

.bp3-icon-filter-open::before{
  content:""; }

.bp3-icon-filter-remove::before{
  content:""; }

.bp3-icon-flag::before{
  content:"⚑"; }

.bp3-icon-flame::before{
  content:""; }

.bp3-icon-flash::before{
  content:""; }

.bp3-icon-floppy-disk::before{
  content:""; }

.bp3-icon-flow-branch::before{
  content:""; }

.bp3-icon-flow-end::before{
  content:""; }

.bp3-icon-flow-linear::before{
  content:""; }

.bp3-icon-flow-review::before{
  content:""; }

.bp3-icon-flow-review-branch::before{
  content:""; }

.bp3-icon-flows::before{
  content:""; }

.bp3-icon-folder-close::before{
  content:""; }

.bp3-icon-folder-new::before{
  content:""; }

.bp3-icon-folder-open::before{
  content:""; }

.bp3-icon-folder-shared::before{
  content:""; }

.bp3-icon-folder-shared-open::before{
  content:""; }

.bp3-icon-follower::before{
  content:""; }

.bp3-icon-following::before{
  content:""; }

.bp3-icon-font::before{
  content:""; }

.bp3-icon-fork::before{
  content:""; }

.bp3-icon-form::before{
  content:""; }

.bp3-icon-full-circle::before{
  content:""; }

.bp3-icon-full-stacked-chart::before{
  content:""; }

.bp3-icon-fullscreen::before{
  content:""; }

.bp3-icon-function::before{
  content:""; }

.bp3-icon-gantt-chart::before{
  content:""; }

.bp3-icon-geolocation::before{
  content:""; }

.bp3-icon-geosearch::before{
  content:""; }

.bp3-icon-git-branch::before{
  content:""; }

.bp3-icon-git-commit::before{
  content:""; }

.bp3-icon-git-merge::before{
  content:""; }

.bp3-icon-git-new-branch::before{
  content:""; }

.bp3-icon-git-pull::before{
  content:""; }

.bp3-icon-git-push::before{
  content:""; }

.bp3-icon-git-repo::before{
  content:""; }

.bp3-icon-glass::before{
  content:""; }

.bp3-icon-globe::before{
  content:""; }

.bp3-icon-globe-network::before{
  content:""; }

.bp3-icon-graph::before{
  content:""; }

.bp3-icon-graph-remove::before{
  content:""; }

.bp3-icon-greater-than::before{
  content:""; }

.bp3-icon-greater-than-or-equal-to::before{
  content:""; }

.bp3-icon-grid::before{
  content:""; }

.bp3-icon-grid-view::before{
  content:""; }

.bp3-icon-group-objects::before{
  content:""; }

.bp3-icon-grouped-bar-chart::before{
  content:""; }

.bp3-icon-hand::before{
  content:""; }

.bp3-icon-hand-down::before{
  content:""; }

.bp3-icon-hand-left::before{
  content:""; }

.bp3-icon-hand-right::before{
  content:""; }

.bp3-icon-hand-up::before{
  content:""; }

.bp3-icon-header::before{
  content:""; }

.bp3-icon-header-one::before{
  content:""; }

.bp3-icon-header-two::before{
  content:""; }

.bp3-icon-headset::before{
  content:""; }

.bp3-icon-heart::before{
  content:"♥"; }

.bp3-icon-heart-broken::before{
  content:""; }

.bp3-icon-heat-grid::before{
  content:""; }

.bp3-icon-heatmap::before{
  content:""; }

.bp3-icon-help::before{
  content:"?"; }

.bp3-icon-helper-management::before{
  content:""; }

.bp3-icon-highlight::before{
  content:""; }

.bp3-icon-history::before{
  content:""; }

.bp3-icon-home::before{
  content:"⌂"; }

.bp3-icon-horizontal-bar-chart::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-asc::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-desc::before{
  content:""; }

.bp3-icon-horizontal-distribution::before{
  content:""; }

.bp3-icon-id-number::before{
  content:""; }

.bp3-icon-image-rotate-left::before{
  content:""; }

.bp3-icon-image-rotate-right::before{
  content:""; }

.bp3-icon-import::before{
  content:""; }

.bp3-icon-inbox::before{
  content:""; }

.bp3-icon-inbox-filtered::before{
  content:""; }

.bp3-icon-inbox-geo::before{
  content:""; }

.bp3-icon-inbox-search::before{
  content:""; }

.bp3-icon-inbox-update::before{
  content:""; }

.bp3-icon-info-sign::before{
  content:"ℹ"; }

.bp3-icon-inheritance::before{
  content:""; }

.bp3-icon-inner-join::before{
  content:""; }

.bp3-icon-insert::before{
  content:""; }

.bp3-icon-intersection::before{
  content:""; }

.bp3-icon-ip-address::before{
  content:""; }

.bp3-icon-issue::before{
  content:""; }

.bp3-icon-issue-closed::before{
  content:""; }

.bp3-icon-issue-new::before{
  content:""; }

.bp3-icon-italic::before{
  content:""; }

.bp3-icon-join-table::before{
  content:""; }

.bp3-icon-key::before{
  content:""; }

.bp3-icon-key-backspace::before{
  content:""; }

.bp3-icon-key-command::before{
  content:""; }

.bp3-icon-key-control::before{
  content:""; }

.bp3-icon-key-delete::before{
  content:""; }

.bp3-icon-key-enter::before{
  content:""; }

.bp3-icon-key-escape::before{
  content:""; }

.bp3-icon-key-option::before{
  content:""; }

.bp3-icon-key-shift::before{
  content:""; }

.bp3-icon-key-tab::before{
  content:""; }

.bp3-icon-known-vehicle::before{
  content:""; }

.bp3-icon-lab-test::before{
  content:""; }

.bp3-icon-label::before{
  content:""; }

.bp3-icon-layer::before{
  content:""; }

.bp3-icon-layers::before{
  content:""; }

.bp3-icon-layout::before{
  content:""; }

.bp3-icon-layout-auto::before{
  content:""; }

.bp3-icon-layout-balloon::before{
  content:""; }

.bp3-icon-layout-circle::before{
  content:""; }

.bp3-icon-layout-grid::before{
  content:""; }

.bp3-icon-layout-group-by::before{
  content:""; }

.bp3-icon-layout-hierarchy::before{
  content:""; }

.bp3-icon-layout-linear::before{
  content:""; }

.bp3-icon-layout-skew-grid::before{
  content:""; }

.bp3-icon-layout-sorted-clusters::before{
  content:""; }

.bp3-icon-learning::before{
  content:""; }

.bp3-icon-left-join::before{
  content:""; }

.bp3-icon-less-than::before{
  content:""; }

.bp3-icon-less-than-or-equal-to::before{
  content:""; }

.bp3-icon-lifesaver::before{
  content:""; }

.bp3-icon-lightbulb::before{
  content:""; }

.bp3-icon-link::before{
  content:""; }

.bp3-icon-list::before{
  content:"☰"; }

.bp3-icon-list-columns::before{
  content:""; }

.bp3-icon-list-detail-view::before{
  content:""; }

.bp3-icon-locate::before{
  content:""; }

.bp3-icon-lock::before{
  content:""; }

.bp3-icon-log-in::before{
  content:""; }

.bp3-icon-log-out::before{
  content:""; }

.bp3-icon-manual::before{
  content:""; }

.bp3-icon-manually-entered-data::before{
  content:""; }

.bp3-icon-map::before{
  content:""; }

.bp3-icon-map-create::before{
  content:""; }

.bp3-icon-map-marker::before{
  content:""; }

.bp3-icon-maximize::before{
  content:""; }

.bp3-icon-media::before{
  content:""; }

.bp3-icon-menu::before{
  content:""; }

.bp3-icon-menu-closed::before{
  content:""; }

.bp3-icon-menu-open::before{
  content:""; }

.bp3-icon-merge-columns::before{
  content:""; }

.bp3-icon-merge-links::before{
  content:""; }

.bp3-icon-minimize::before{
  content:""; }

.bp3-icon-minus::before{
  content:"−"; }

.bp3-icon-mobile-phone::before{
  content:""; }

.bp3-icon-mobile-video::before{
  content:""; }

.bp3-icon-moon::before{
  content:""; }

.bp3-icon-more::before{
  content:""; }

.bp3-icon-mountain::before{
  content:""; }

.bp3-icon-move::before{
  content:""; }

.bp3-icon-mugshot::before{
  content:""; }

.bp3-icon-multi-select::before{
  content:""; }

.bp3-icon-music::before{
  content:""; }

.bp3-icon-new-drawing::before{
  content:""; }

.bp3-icon-new-grid-item::before{
  content:""; }

.bp3-icon-new-layer::before{
  content:""; }

.bp3-icon-new-layers::before{
  content:""; }

.bp3-icon-new-link::before{
  content:""; }

.bp3-icon-new-object::before{
  content:""; }

.bp3-icon-new-person::before{
  content:""; }

.bp3-icon-new-prescription::before{
  content:""; }

.bp3-icon-new-text-box::before{
  content:""; }

.bp3-icon-ninja::before{
  content:""; }

.bp3-icon-not-equal-to::before{
  content:""; }

.bp3-icon-notifications::before{
  content:""; }

.bp3-icon-notifications-updated::before{
  content:""; }

.bp3-icon-numbered-list::before{
  content:""; }

.bp3-icon-numerical::before{
  content:""; }

.bp3-icon-office::before{
  content:""; }

.bp3-icon-offline::before{
  content:""; }

.bp3-icon-oil-field::before{
  content:""; }

.bp3-icon-one-column::before{
  content:""; }

.bp3-icon-outdated::before{
  content:""; }

.bp3-icon-page-layout::before{
  content:""; }

.bp3-icon-panel-stats::before{
  content:""; }

.bp3-icon-panel-table::before{
  content:""; }

.bp3-icon-paperclip::before{
  content:""; }

.bp3-icon-paragraph::before{
  content:""; }

.bp3-icon-path::before{
  content:""; }

.bp3-icon-path-search::before{
  content:""; }

.bp3-icon-pause::before{
  content:""; }

.bp3-icon-people::before{
  content:""; }

.bp3-icon-percentage::before{
  content:""; }

.bp3-icon-person::before{
  content:""; }

.bp3-icon-phone::before{
  content:"☎"; }

.bp3-icon-pie-chart::before{
  content:""; }

.bp3-icon-pin::before{
  content:""; }

.bp3-icon-pivot::before{
  content:""; }

.bp3-icon-pivot-table::before{
  content:""; }

.bp3-icon-play::before{
  content:""; }

.bp3-icon-plus::before{
  content:"+"; }

.bp3-icon-polygon-filter::before{
  content:""; }

.bp3-icon-power::before{
  content:""; }

.bp3-icon-predictive-analysis::before{
  content:""; }

.bp3-icon-prescription::before{
  content:""; }

.bp3-icon-presentation::before{
  content:""; }

.bp3-icon-print::before{
  content:"⎙"; }

.bp3-icon-projects::before{
  content:""; }

.bp3-icon-properties::before{
  content:""; }

.bp3-icon-property::before{
  content:""; }

.bp3-icon-publish-function::before{
  content:""; }

.bp3-icon-pulse::before{
  content:""; }

.bp3-icon-random::before{
  content:""; }

.bp3-icon-record::before{
  content:""; }

.bp3-icon-redo::before{
  content:""; }

.bp3-icon-refresh::before{
  content:""; }

.bp3-icon-regression-chart::before{
  content:""; }

.bp3-icon-remove::before{
  content:""; }

.bp3-icon-remove-column::before{
  content:""; }

.bp3-icon-remove-column-left::before{
  content:""; }

.bp3-icon-remove-column-right::before{
  content:""; }

.bp3-icon-remove-row-bottom::before{
  content:""; }

.bp3-icon-remove-row-top::before{
  content:""; }

.bp3-icon-repeat::before{
  content:""; }

.bp3-icon-reset::before{
  content:""; }

.bp3-icon-resolve::before{
  content:""; }

.bp3-icon-rig::before{
  content:""; }

.bp3-icon-right-join::before{
  content:""; }

.bp3-icon-ring::before{
  content:""; }

.bp3-icon-rotate-document::before{
  content:""; }

.bp3-icon-rotate-page::before{
  content:""; }

.bp3-icon-satellite::before{
  content:""; }

.bp3-icon-saved::before{
  content:""; }

.bp3-icon-scatter-plot::before{
  content:""; }

.bp3-icon-search::before{
  content:""; }

.bp3-icon-search-around::before{
  content:""; }

.bp3-icon-search-template::before{
  content:""; }

.bp3-icon-search-text::before{
  content:""; }

.bp3-icon-segmented-control::before{
  content:""; }

.bp3-icon-select::before{
  content:""; }

.bp3-icon-selection::before{
  content:"⦿"; }

.bp3-icon-send-to::before{
  content:""; }

.bp3-icon-send-to-graph::before{
  content:""; }

.bp3-icon-send-to-map::before{
  content:""; }

.bp3-icon-series-add::before{
  content:""; }

.bp3-icon-series-configuration::before{
  content:""; }

.bp3-icon-series-derived::before{
  content:""; }

.bp3-icon-series-filtered::before{
  content:""; }

.bp3-icon-series-search::before{
  content:""; }

.bp3-icon-settings::before{
  content:""; }

.bp3-icon-share::before{
  content:""; }

.bp3-icon-shield::before{
  content:""; }

.bp3-icon-shop::before{
  content:""; }

.bp3-icon-shopping-cart::before{
  content:""; }

.bp3-icon-signal-search::before{
  content:""; }

.bp3-icon-sim-card::before{
  content:""; }

.bp3-icon-slash::before{
  content:""; }

.bp3-icon-small-cross::before{
  content:""; }

.bp3-icon-small-minus::before{
  content:""; }

.bp3-icon-small-plus::before{
  content:""; }

.bp3-icon-small-tick::before{
  content:""; }

.bp3-icon-snowflake::before{
  content:""; }

.bp3-icon-social-media::before{
  content:""; }

.bp3-icon-sort::before{
  content:""; }

.bp3-icon-sort-alphabetical::before{
  content:""; }

.bp3-icon-sort-alphabetical-desc::before{
  content:""; }

.bp3-icon-sort-asc::before{
  content:""; }

.bp3-icon-sort-desc::before{
  content:""; }

.bp3-icon-sort-numerical::before{
  content:""; }

.bp3-icon-sort-numerical-desc::before{
  content:""; }

.bp3-icon-split-columns::before{
  content:""; }

.bp3-icon-square::before{
  content:""; }

.bp3-icon-stacked-chart::before{
  content:""; }

.bp3-icon-star::before{
  content:"★"; }

.bp3-icon-star-empty::before{
  content:"☆"; }

.bp3-icon-step-backward::before{
  content:""; }

.bp3-icon-step-chart::before{
  content:""; }

.bp3-icon-step-forward::before{
  content:""; }

.bp3-icon-stop::before{
  content:""; }

.bp3-icon-stopwatch::before{
  content:""; }

.bp3-icon-strikethrough::before{
  content:""; }

.bp3-icon-style::before{
  content:""; }

.bp3-icon-swap-horizontal::before{
  content:""; }

.bp3-icon-swap-vertical::before{
  content:""; }

.bp3-icon-symbol-circle::before{
  content:""; }

.bp3-icon-symbol-cross::before{
  content:""; }

.bp3-icon-symbol-diamond::before{
  content:""; }

.bp3-icon-symbol-square::before{
  content:""; }

.bp3-icon-symbol-triangle-down::before{
  content:""; }

.bp3-icon-symbol-triangle-up::before{
  content:""; }

.bp3-icon-tag::before{
  content:""; }

.bp3-icon-take-action::before{
  content:""; }

.bp3-icon-taxi::before{
  content:""; }

.bp3-icon-text-highlight::before{
  content:""; }

.bp3-icon-th::before{
  content:""; }

.bp3-icon-th-derived::before{
  content:""; }

.bp3-icon-th-disconnect::before{
  content:""; }

.bp3-icon-th-filtered::before{
  content:""; }

.bp3-icon-th-list::before{
  content:""; }

.bp3-icon-thumbs-down::before{
  content:""; }

.bp3-icon-thumbs-up::before{
  content:""; }

.bp3-icon-tick::before{
  content:"✓"; }

.bp3-icon-tick-circle::before{
  content:""; }

.bp3-icon-time::before{
  content:"⏲"; }

.bp3-icon-timeline-area-chart::before{
  content:""; }

.bp3-icon-timeline-bar-chart::before{
  content:""; }

.bp3-icon-timeline-events::before{
  content:""; }

.bp3-icon-timeline-line-chart::before{
  content:""; }

.bp3-icon-tint::before{
  content:""; }

.bp3-icon-torch::before{
  content:""; }

.bp3-icon-tractor::before{
  content:""; }

.bp3-icon-train::before{
  content:""; }

.bp3-icon-translate::before{
  content:""; }

.bp3-icon-trash::before{
  content:""; }

.bp3-icon-tree::before{
  content:""; }

.bp3-icon-trending-down::before{
  content:""; }

.bp3-icon-trending-up::before{
  content:""; }

.bp3-icon-truck::before{
  content:""; }

.bp3-icon-two-columns::before{
  content:""; }

.bp3-icon-unarchive::before{
  content:""; }

.bp3-icon-underline::before{
  content:"⎁"; }

.bp3-icon-undo::before{
  content:"⎌"; }

.bp3-icon-ungroup-objects::before{
  content:""; }

.bp3-icon-unknown-vehicle::before{
  content:""; }

.bp3-icon-unlock::before{
  content:""; }

.bp3-icon-unpin::before{
  content:""; }

.bp3-icon-unresolve::before{
  content:""; }

.bp3-icon-updated::before{
  content:""; }

.bp3-icon-upload::before{
  content:""; }

.bp3-icon-user::before{
  content:""; }

.bp3-icon-variable::before{
  content:""; }

.bp3-icon-vertical-bar-chart-asc::before{
  content:""; }

.bp3-icon-vertical-bar-chart-desc::before{
  content:""; }

.bp3-icon-vertical-distribution::before{
  content:""; }

.bp3-icon-video::before{
  content:""; }

.bp3-icon-volume-down::before{
  content:""; }

.bp3-icon-volume-off::before{
  content:""; }

.bp3-icon-volume-up::before{
  content:""; }

.bp3-icon-walk::before{
  content:""; }

.bp3-icon-warning-sign::before{
  content:""; }

.bp3-icon-waterfall-chart::before{
  content:""; }

.bp3-icon-widget::before{
  content:""; }

.bp3-icon-widget-button::before{
  content:""; }

.bp3-icon-widget-footer::before{
  content:""; }

.bp3-icon-widget-header::before{
  content:""; }

.bp3-icon-wrench::before{
  content:""; }

.bp3-icon-zoom-in::before{
  content:""; }

.bp3-icon-zoom-out::before{
  content:""; }

.bp3-icon-zoom-to-fit::before{
  content:""; }
.bp3-submenu > .bp3-popover-wrapper{
  display:block; }

.bp3-submenu .bp3-popover-target{
  display:block; }
  .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{ }

.bp3-submenu.bp3-popover{
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0 5px; }
  .bp3-submenu.bp3-popover > .bp3-popover-content{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-submenu.bp3-popover, .bp3-submenu.bp3-popover.bp3-dark{
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-dark .bp3-submenu.bp3-popover > .bp3-popover-content, .bp3-submenu.bp3-popover.bp3-dark > .bp3-popover-content{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
.bp3-menu{
  background:#ffffff;
  border-radius:3px;
  color:#182026;
  list-style:none;
  margin:0;
  min-width:180px;
  padding:5px;
  text-align:left; }

.bp3-menu-divider{
  border-top:1px solid rgba(16, 22, 26, 0.15);
  display:block;
  margin:5px; }
  .bp3-dark .bp3-menu-divider{
    border-top-color:rgba(255, 255, 255, 0.15); }

.bp3-menu-item{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  border-radius:2px;
  color:inherit;
  line-height:20px;
  padding:5px 7px;
  text-decoration:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-menu-item > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-menu-item > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-menu-item::before,
  .bp3-menu-item > *{
    margin-right:7px; }
  .bp3-menu-item:empty::before,
  .bp3-menu-item > :last-child{
    margin-right:0; }
  .bp3-menu-item > .bp3-fill{
    word-break:break-word; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    background-color:rgba(167, 182, 194, 0.3);
    cursor:pointer;
    text-decoration:none; }
  .bp3-menu-item.bp3-disabled{
    background-color:inherit;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-dark .bp3-menu-item{
    color:inherit; }
    .bp3-dark .bp3-menu-item:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
      background-color:rgba(138, 155, 168, 0.15);
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-disabled{
      background-color:inherit;
      color:rgba(167, 182, 194, 0.6); }
  .bp3-menu-item.bp3-intent-primary{
    color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-primary::before, .bp3-menu-item.bp3-intent-primary::after,
    .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
      color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary.bp3-active{
      background-color:#137cbd; }
    .bp3-menu-item.bp3-intent-primary:active{
      background-color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary:active, .bp3-menu-item.bp3-intent-primary:active::before, .bp3-menu-item.bp3-intent-primary:active::after,
    .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-menu-item.bp3-intent-primary.bp3-active::after,
    .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-success{
    color:#0d8050; }
    .bp3-menu-item.bp3-intent-success .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-success::before, .bp3-menu-item.bp3-intent-success::after,
    .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
      color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success.bp3-active{
      background-color:#0f9960; }
    .bp3-menu-item.bp3-intent-success:active{
      background-color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-menu-item.bp3-intent-success:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success:active, .bp3-menu-item.bp3-intent-success:active::before, .bp3-menu-item.bp3-intent-success:active::after,
    .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-menu-item.bp3-intent-success.bp3-active::after,
    .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-warning{
    color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-warning::before, .bp3-menu-item.bp3-intent-warning::after,
    .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
      color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning.bp3-active{
      background-color:#d9822b; }
    .bp3-menu-item.bp3-intent-warning:active{
      background-color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning:active, .bp3-menu-item.bp3-intent-warning:active::before, .bp3-menu-item.bp3-intent-warning:active::after,
    .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-menu-item.bp3-intent-warning.bp3-active::after,
    .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-danger{
    color:#c23030; }
    .bp3-menu-item.bp3-intent-danger .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-danger::before, .bp3-menu-item.bp3-intent-danger::after,
    .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
      color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger.bp3-active{
      background-color:#db3737; }
    .bp3-menu-item.bp3-intent-danger:active{
      background-color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger:active, .bp3-menu-item.bp3-intent-danger:active::before, .bp3-menu-item.bp3-intent-danger:active::after,
    .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-menu-item.bp3-intent-danger.bp3-active::after,
    .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    margin-right:7px; }
  .bp3-menu-item::before,
  .bp3-menu-item > .bp3-icon{
    color:#5c7080;
    margin-top:2px; }
  .bp3-menu-item .bp3-menu-item-label{
    color:#5c7080; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    color:inherit; }
  .bp3-menu-item.bp3-active, .bp3-menu-item:active{
    background-color:rgba(115, 134, 148, 0.3); }
  .bp3-menu-item.bp3-disabled{
    background-color:inherit !important;
    color:rgba(92, 112, 128, 0.6) !important;
    cursor:not-allowed !important;
    outline:none !important; }
    .bp3-menu-item.bp3-disabled::before,
    .bp3-menu-item.bp3-disabled > .bp3-icon,
    .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-large .bp3-menu-item{
    font-size:16px;
    line-height:22px;
    padding:9px 7px; }
    .bp3-large .bp3-menu-item .bp3-icon{
      margin-top:3px; }
    .bp3-large .bp3-menu-item::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      margin-right:10px;
      margin-top:1px; }

button.bp3-menu-item{
  background:none;
  border:none;
  text-align:left;
  width:100%; }
.bp3-menu-header{
  border-top:1px solid rgba(16, 22, 26, 0.15);
  display:block;
  margin:5px;
  cursor:default;
  padding-left:2px; }
  .bp3-dark .bp3-menu-header{
    border-top-color:rgba(255, 255, 255, 0.15); }
  .bp3-menu-header:first-of-type{
    border-top:none; }
  .bp3-menu-header > h6{
    color:#182026;
    font-weight:600;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    line-height:17px;
    margin:0;
    padding:10px 7px 0 1px; }
    .bp3-dark .bp3-menu-header > h6{
      color:#f5f8fa; }
  .bp3-menu-header:first-of-type > h6{
    padding-top:0; }
  .bp3-large .bp3-menu-header > h6{
    font-size:18px;
    padding-bottom:5px;
    padding-top:15px; }
  .bp3-large .bp3-menu-header:first-of-type > h6{
    padding-top:0; }

.bp3-dark .bp3-menu{
  background:#30404d;
  color:#f5f8fa; }

.bp3-dark .bp3-menu-item{ }
  .bp3-dark .bp3-menu-item.bp3-intent-primary{
    color:#48aff0; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary::before, .bp3-dark .bp3-menu-item.bp3-intent-primary::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
      color:#48aff0; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active{
      background-color:#137cbd; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:active{
      background-color:#106ba3; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary:active, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-success{
    color:#3dcc91; }
    .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-success::before, .bp3-dark .bp3-menu-item.bp3-intent-success::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
      color:#3dcc91; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active{
      background-color:#0f9960; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:active{
      background-color:#0d8050; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success:active, .bp3-dark .bp3-menu-item.bp3-intent-success:active::before, .bp3-dark .bp3-menu-item.bp3-intent-success:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning{
    color:#ffb366; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning::before, .bp3-dark .bp3-menu-item.bp3-intent-warning::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
      color:#ffb366; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active{
      background-color:#d9822b; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:active{
      background-color:#bf7326; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning:active, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger{
    color:#ff7373; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger::before, .bp3-dark .bp3-menu-item.bp3-intent-danger::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
      color:#ff7373; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active{
      background-color:#db3737; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:active{
      background-color:#c23030; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger:active, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item::before,
  .bp3-dark .bp3-menu-item > .bp3-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-menu-item .bp3-menu-item-label{
    color:#a7b6c2; }
  .bp3-dark .bp3-menu-item.bp3-active, .bp3-dark .bp3-menu-item:active{
    background-color:rgba(138, 155, 168, 0.3); }
  .bp3-dark .bp3-menu-item.bp3-disabled{
    color:rgba(167, 182, 194, 0.6) !important; }
    .bp3-dark .bp3-menu-item.bp3-disabled::before,
    .bp3-dark .bp3-menu-item.bp3-disabled > .bp3-icon,
    .bp3-dark .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
      color:rgba(167, 182, 194, 0.6) !important; }

.bp3-dark .bp3-menu-divider,
.bp3-dark .bp3-menu-header{
  border-color:rgba(255, 255, 255, 0.15); }

.bp3-dark .bp3-menu-header > h6{
  color:#f5f8fa; }

.bp3-label .bp3-menu{
  margin-top:5px; }
.bp3-navbar{
  background-color:#ffffff;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  height:50px;
  padding:0 15px;
  position:relative;
  width:100%;
  z-index:10; }
  .bp3-navbar.bp3-dark,
  .bp3-dark .bp3-navbar{
    background-color:#394b59; }
  .bp3-navbar.bp3-dark{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-navbar{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-navbar.bp3-fixed-top{
    left:0;
    position:fixed;
    right:0;
    top:0; }

.bp3-navbar-heading{
  font-size:16px;
  margin-right:15px; }

.bp3-navbar-group{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:50px; }
  .bp3-navbar-group.bp3-align-left{
    float:left; }
  .bp3-navbar-group.bp3-align-right{
    float:right; }

.bp3-navbar-divider{
  border-left:1px solid rgba(16, 22, 26, 0.15);
  height:20px;
  margin:0 10px; }
  .bp3-dark .bp3-navbar-divider{
    border-left-color:rgba(255, 255, 255, 0.15); }
.bp3-non-ideal-state{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  height:100%;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  text-align:center;
  width:100%; }
  .bp3-non-ideal-state > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-non-ideal-state > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-non-ideal-state::before,
  .bp3-non-ideal-state > *{
    margin-bottom:20px; }
  .bp3-non-ideal-state:empty::before,
  .bp3-non-ideal-state > :last-child{
    margin-bottom:0; }
  .bp3-non-ideal-state > *{
    max-width:400px; }

.bp3-non-ideal-state-visual{
  color:rgba(92, 112, 128, 0.6);
  font-size:60px; }
  .bp3-dark .bp3-non-ideal-state-visual{
    color:rgba(167, 182, 194, 0.6); }

.bp3-overflow-list{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:nowrap;
      flex-wrap:nowrap;
  min-width:0; }

.bp3-overflow-list-spacer{
  -ms-flex-negative:1;
      flex-shrink:1;
  width:1px; }

body.bp3-overlay-open{
  overflow:hidden; }

.bp3-overlay{
  bottom:0;
  left:0;
  position:static;
  right:0;
  top:0;
  z-index:20; }
  .bp3-overlay:not(.bp3-overlay-open){
    pointer-events:none; }
  .bp3-overlay.bp3-overlay-container{
    overflow:hidden;
    position:fixed; }
    .bp3-overlay.bp3-overlay-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-scroll-container{
    overflow:auto;
    position:fixed; }
    .bp3-overlay.bp3-overlay-scroll-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-inline{
    display:inline;
    overflow:visible; }

.bp3-overlay-content{
  position:fixed;
  z-index:20; }
  .bp3-overlay-inline .bp3-overlay-content,
  .bp3-overlay-scroll-container .bp3-overlay-content{
    position:absolute; }

.bp3-overlay-backdrop{
  bottom:0;
  left:0;
  position:fixed;
  right:0;
  top:0;
  opacity:1;
  background-color:rgba(16, 22, 26, 0.7);
  overflow:auto;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none;
  z-index:20; }
  .bp3-overlay-backdrop.bp3-overlay-enter, .bp3-overlay-backdrop.bp3-overlay-appear{
    opacity:0; }
  .bp3-overlay-backdrop.bp3-overlay-enter-active, .bp3-overlay-backdrop.bp3-overlay-appear-active{
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-overlay-backdrop.bp3-overlay-exit{
    opacity:1; }
  .bp3-overlay-backdrop.bp3-overlay-exit-active{
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-overlay-backdrop:focus{
    outline:none; }
  .bp3-overlay-inline .bp3-overlay-backdrop{
    position:absolute; }
.bp3-panel-stack{
  overflow:hidden;
  position:relative; }

.bp3-panel-stack-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
          box-shadow:0 1px rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-negative:0;
      flex-shrink:0;
  height:30px;
  z-index:1; }
  .bp3-dark .bp3-panel-stack-header{
    -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 1px rgba(255, 255, 255, 0.15); }
  .bp3-panel-stack-header > span{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1;
            flex:1; }
  .bp3-panel-stack-header .bp3-heading{
    margin:0 5px; }

.bp3-button.bp3-panel-stack-header-back{
  margin-left:5px;
  padding-left:0;
  white-space:nowrap; }
  .bp3-button.bp3-panel-stack-header-back .bp3-icon{
    margin:0 2px; }

.bp3-panel-stack-view{
  bottom:0;
  left:0;
  position:absolute;
  right:0;
  top:0;
  background-color:#ffffff;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin-right:-1px;
  overflow-y:auto;
  z-index:1; }
  .bp3-dark .bp3-panel-stack-view{
    background-color:#30404d; }
  .bp3-panel-stack-view:nth-last-child(n + 4){
    display:none; }

.bp3-panel-stack-push .bp3-panel-stack-enter, .bp3-panel-stack-push .bp3-panel-stack-appear{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0; }

.bp3-panel-stack-push .bp3-panel-stack-enter-active, .bp3-panel-stack-push .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-push .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-push .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-pop .bp3-panel-stack-enter, .bp3-panel-stack-pop .bp3-panel-stack-appear{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0; }

.bp3-panel-stack-pop .bp3-panel-stack-enter-active, .bp3-panel-stack-pop .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-pop .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-pop .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }
.bp3-panel-stack2{
  overflow:hidden;
  position:relative; }

.bp3-panel-stack2-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
          box-shadow:0 1px rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-negative:0;
      flex-shrink:0;
  height:30px;
  z-index:1; }
  .bp3-dark .bp3-panel-stack2-header{
    -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 1px rgba(255, 255, 255, 0.15); }
  .bp3-panel-stack2-header > span{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1;
            flex:1; }
  .bp3-panel-stack2-header .bp3-heading{
    margin:0 5px; }

.bp3-button.bp3-panel-stack2-header-back{
  margin-left:5px;
  padding-left:0;
  white-space:nowrap; }
  .bp3-button.bp3-panel-stack2-header-back .bp3-icon{
    margin:0 2px; }

.bp3-panel-stack2-view{
  bottom:0;
  left:0;
  position:absolute;
  right:0;
  top:0;
  background-color:#ffffff;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin-right:-1px;
  overflow-y:auto;
  z-index:1; }
  .bp3-dark .bp3-panel-stack2-view{
    background-color:#30404d; }
  .bp3-panel-stack2-view:nth-last-child(n + 4){
    display:none; }

.bp3-panel-stack2-push .bp3-panel-stack2-enter, .bp3-panel-stack2-push .bp3-panel-stack2-appear{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0; }

.bp3-panel-stack2-push .bp3-panel-stack2-enter-active, .bp3-panel-stack2-push .bp3-panel-stack2-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-push .bp3-panel-stack2-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack2-push .bp3-panel-stack2-exit-active{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-pop .bp3-panel-stack2-enter, .bp3-panel-stack2-pop .bp3-panel-stack2-appear{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0; }

.bp3-panel-stack2-pop .bp3-panel-stack2-enter-active, .bp3-panel-stack2-pop .bp3-panel-stack2-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-pop .bp3-panel-stack2-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack2-pop .bp3-panel-stack2-exit-active{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }
.bp3-popover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1);
  border-radius:3px;
  display:inline-block;
  z-index:20; }
  .bp3-popover .bp3-popover-arrow{
    height:30px;
    position:absolute;
    width:30px; }
    .bp3-popover .bp3-popover-arrow::before{
      height:20px;
      margin:5px;
      width:20px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover{
    margin-bottom:17px;
    margin-top:-17px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
      bottom:-11px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover{
    margin-left:17px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
      left:-11px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover{
    margin-top:17px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
      top:-11px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover{
    margin-left:-17px;
    margin-right:17px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
      right:-11px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-popover > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-popover > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
    top:-0.3934px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
    right:-0.3934px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
    left:-0.3934px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
    bottom:-0.3934px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-popover .bp3-popover-content{
    background:#ffffff;
    color:inherit; }
  .bp3-popover .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-popover .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-popover .bp3-popover-arrow-fill{
    fill:#ffffff; }
  .bp3-popover-enter > .bp3-popover, .bp3-popover-appear > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3); }
  .bp3-popover-enter-active > .bp3-popover, .bp3-popover-appear-active > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-popover-exit > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-popover .bp3-popover-content{
    border-radius:3px;
    position:relative; }
  .bp3-popover.bp3-popover-content-sizing .bp3-popover-content{
    max-width:350px;
    padding:20px; }
  .bp3-popover-target + .bp3-overlay .bp3-popover.bp3-popover-content-sizing{
    width:350px; }
  .bp3-popover.bp3-minimal{
    margin:0 !important; }
    .bp3-popover.bp3-minimal .bp3-popover-arrow{
      display:none; }
    .bp3-popover.bp3-minimal.bp3-popover{
      -webkit-transform:scale(1);
              transform:scale(1); }
      .bp3-popover-enter > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-enter-active > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-popover-exit > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-exit-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-popover.bp3-dark,
  .bp3-dark .bp3-popover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-popover .bp3-popover-content{
      background:#30404d;
      color:inherit; }
    .bp3-popover.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-popover .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-popover .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-popover.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-popover .bp3-popover-arrow-fill{
      fill:#30404d; }

.bp3-popover-arrow::before{
  border-radius:2px;
  content:"";
  display:block;
  position:absolute;
  -webkit-transform:rotate(45deg);
          transform:rotate(45deg); }

.bp3-tether-pinned .bp3-popover-arrow{
  display:none; }

.bp3-popover-backdrop{
  background:rgba(255, 255, 255, 0); }

.bp3-transition-container{
  opacity:1;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  z-index:20; }
  .bp3-transition-container.bp3-popover-enter, .bp3-transition-container.bp3-popover-appear{
    opacity:0; }
  .bp3-transition-container.bp3-popover-enter-active, .bp3-transition-container.bp3-popover-appear-active{
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-transition-container.bp3-popover-exit{
    opacity:1; }
  .bp3-transition-container.bp3-popover-exit-active{
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-transition-container:focus{
    outline:none; }
  .bp3-transition-container.bp3-popover-leave .bp3-popover-content{
    pointer-events:none; }
  .bp3-transition-container[data-x-out-of-boundaries]{
    display:none; }

span.bp3-popover-target{
  display:inline-block; }

.bp3-popover-wrapper.bp3-fill{
  width:100%; }

.bp3-portal{
  left:0;
  position:absolute;
  right:0;
  top:0; }
@-webkit-keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }
@keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }

.bp3-progress-bar{
  background:rgba(92, 112, 128, 0.2);
  border-radius:40px;
  display:block;
  height:8px;
  overflow:hidden;
  position:relative;
  width:100%; }
  .bp3-progress-bar .bp3-progress-meter{
    background:linear-gradient(-45deg, rgba(255, 255, 255, 0.2) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.2) 50%, rgba(255, 255, 255, 0.2) 75%, transparent 75%);
    background-color:rgba(92, 112, 128, 0.8);
    background-size:30px 30px;
    border-radius:40px;
    height:100%;
    position:absolute;
    -webkit-transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    width:100%; }
  .bp3-progress-bar:not(.bp3-no-animation):not(.bp3-no-stripes) .bp3-progress-meter{
    animation:linear-progress-bar-stripes 300ms linear infinite reverse; }
  .bp3-progress-bar.bp3-no-stripes .bp3-progress-meter{
    background-image:none; }

.bp3-dark .bp3-progress-bar{
  background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-progress-bar .bp3-progress-meter{
    background-color:#8a9ba8; }

.bp3-progress-bar.bp3-intent-primary .bp3-progress-meter{
  background-color:#137cbd; }

.bp3-progress-bar.bp3-intent-success .bp3-progress-meter{
  background-color:#0f9960; }

.bp3-progress-bar.bp3-intent-warning .bp3-progress-meter{
  background-color:#d9822b; }

.bp3-progress-bar.bp3-intent-danger .bp3-progress-meter{
  background-color:#db3737; }
@-webkit-keyframes skeleton-glow{
  from{
    background:rgba(206, 217, 224, 0.2);
    border-color:rgba(206, 217, 224, 0.2); }
  to{
    background:rgba(92, 112, 128, 0.2);
    border-color:rgba(92, 112, 128, 0.2); } }
@keyframes skeleton-glow{
  from{
    background:rgba(206, 217, 224, 0.2);
    border-color:rgba(206, 217, 224, 0.2); }
  to{
    background:rgba(92, 112, 128, 0.2);
    border-color:rgba(92, 112, 128, 0.2); } }
.bp3-skeleton{
  -webkit-animation:1000ms linear infinite alternate skeleton-glow;
          animation:1000ms linear infinite alternate skeleton-glow;
  background:rgba(206, 217, 224, 0.2);
  background-clip:padding-box !important;
  border-color:rgba(206, 217, 224, 0.2) !important;
  border-radius:2px;
  -webkit-box-shadow:none !important;
          box-shadow:none !important;
  color:transparent !important;
  cursor:default;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-skeleton::before, .bp3-skeleton::after,
  .bp3-skeleton *{
    visibility:hidden !important; }
.bp3-slider{
  height:40px;
  min-width:150px;
  width:100%;
  cursor:default;
  outline:none;
  position:relative;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-slider:hover{
    cursor:pointer; }
  .bp3-slider:active{
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-slider.bp3-disabled{
    cursor:not-allowed;
    opacity:0.5; }
  .bp3-slider.bp3-slider-unlabeled{
    height:16px; }

.bp3-slider-track,
.bp3-slider-progress{
  height:6px;
  left:0;
  right:0;
  top:5px;
  position:absolute; }

.bp3-slider-track{
  border-radius:3px;
  overflow:hidden; }

.bp3-slider-progress{
  background:rgba(92, 112, 128, 0.2); }
  .bp3-dark .bp3-slider-progress{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-slider-progress.bp3-intent-primary{
    background-color:#137cbd; }
  .bp3-slider-progress.bp3-intent-success{
    background-color:#0f9960; }
  .bp3-slider-progress.bp3-intent-warning{
    background-color:#d9822b; }
  .bp3-slider-progress.bp3-intent-danger{
    background-color:#db3737; }

.bp3-slider-handle{
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  color:#182026;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
  cursor:pointer;
  height:16px;
  left:0;
  position:absolute;
  top:0;
  width:16px; }
  .bp3-slider-handle:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-slider-handle:active, .bp3-slider-handle.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-slider-handle:disabled, .bp3-slider-handle.bp3-disabled{
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    outline:none; }
    .bp3-slider-handle:disabled.bp3-active, .bp3-slider-handle:disabled.bp3-active:hover, .bp3-slider-handle.bp3-disabled.bp3-active, .bp3-slider-handle.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }
  .bp3-slider-handle:focus{
    z-index:1; }
  .bp3-slider-handle:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
    cursor:-webkit-grab;
    cursor:grab;
    z-index:2; }
  .bp3-slider-handle.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-disabled .bp3-slider-handle{
    background:#bfccd6;
    -webkit-box-shadow:none;
            box-shadow:none;
    pointer-events:none; }
  .bp3-dark .bp3-slider-handle{
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover, .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-slider-handle:disabled, .bp3-dark .bp3-slider-handle.bp3-disabled{
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-slider-handle:disabled.bp3-active, .bp3-dark .bp3-slider-handle.bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-slider-handle .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-slider-handle, .bp3-dark .bp3-slider-handle:hover{
      background-color:#394b59; }
    .bp3-dark .bp3-slider-handle.bp3-active{
      background-color:#293742; }
  .bp3-dark .bp3-disabled .bp3-slider-handle{
    background:#5c7080;
    border-color:#5c7080;
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-slider-handle .bp3-slider-label{
    background:#394b59;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    color:#f5f8fa;
    margin-left:8px; }
    .bp3-dark .bp3-slider-handle .bp3-slider-label{
      background:#e1e8ed;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
      color:#394b59; }
    .bp3-disabled .bp3-slider-handle .bp3-slider-label{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-slider-handle.bp3-start, .bp3-slider-handle.bp3-end{
    width:8px; }
  .bp3-slider-handle.bp3-start{
    border-bottom-right-radius:0;
    border-top-right-radius:0; }
  .bp3-slider-handle.bp3-end{
    border-bottom-left-radius:0;
    border-top-left-radius:0;
    margin-left:8px; }
    .bp3-slider-handle.bp3-end .bp3-slider-label{
      margin-left:0; }

.bp3-slider-label{
  -webkit-transform:translate(-50%, 20px);
          transform:translate(-50%, 20px);
  display:inline-block;
  font-size:12px;
  line-height:1;
  padding:2px 5px;
  position:absolute;
  vertical-align:top; }

.bp3-slider.bp3-vertical{
  height:150px;
  min-width:40px;
  width:40px; }
  .bp3-slider.bp3-vertical .bp3-slider-track,
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    bottom:0;
    height:auto;
    left:5px;
    top:0;
    width:6px; }
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    top:auto; }
  .bp3-slider.bp3-vertical .bp3-slider-label{
    -webkit-transform:translate(20px, 50%);
            transform:translate(20px, 50%); }
  .bp3-slider.bp3-vertical .bp3-slider-handle{
    top:auto; }
    .bp3-slider.bp3-vertical .bp3-slider-handle .bp3-slider-label{
      margin-left:0;
      margin-top:-8px; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end, .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      height:8px;
      margin-left:0;
      width:16px; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      border-bottom-right-radius:3px;
      border-top-left-radius:0; }
      .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start .bp3-slider-label{
        -webkit-transform:translate(20px);
                transform:translate(20px); }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end{
      border-bottom-left-radius:0;
      border-bottom-right-radius:0;
      border-top-left-radius:3px;
      margin-bottom:8px; }

@-webkit-keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

@keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

.bp3-spinner{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  overflow:visible;
  vertical-align:middle; }
  .bp3-spinner svg{
    display:block; }
  .bp3-spinner path{
    fill-opacity:0; }
  .bp3-spinner .bp3-spinner-head{
    stroke:rgba(92, 112, 128, 0.8);
    stroke-linecap:round;
    -webkit-transform-origin:center;
            transform-origin:center;
    -webkit-transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-spinner .bp3-spinner-track{
    stroke:rgba(92, 112, 128, 0.2); }

.bp3-spinner-animation{
  -webkit-animation:pt-spinner-animation 500ms linear infinite;
          animation:pt-spinner-animation 500ms linear infinite; }
  .bp3-no-spin > .bp3-spinner-animation{
    -webkit-animation:none;
            animation:none; }

.bp3-dark .bp3-spinner .bp3-spinner-head{
  stroke:#8a9ba8; }

.bp3-dark .bp3-spinner .bp3-spinner-track{
  stroke:rgba(16, 22, 26, 0.5); }

.bp3-spinner.bp3-intent-primary .bp3-spinner-head{
  stroke:#137cbd; }

.bp3-spinner.bp3-intent-success .bp3-spinner-head{
  stroke:#0f9960; }

.bp3-spinner.bp3-intent-warning .bp3-spinner-head{
  stroke:#d9822b; }

.bp3-spinner.bp3-intent-danger .bp3-spinner-head{
  stroke:#db3737; }
.bp3-tabs.bp3-vertical{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-tabs.bp3-vertical > .bp3-tab-list{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab{
      border-radius:3px;
      padding:0 10px;
      width:100%; }
      .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab[aria-selected="true"]{
        background-color:rgba(19, 124, 189, 0.2);
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab-indicator-wrapper .bp3-tab-indicator{
      background-color:rgba(19, 124, 189, 0.2);
      border-radius:3px;
      bottom:0;
      height:auto;
      left:0;
      right:0;
      top:0; }
  .bp3-tabs.bp3-vertical > .bp3-tab-panel{
    margin-top:0;
    padding-left:20px; }

.bp3-tab-list{
  -webkit-box-align:end;
      -ms-flex-align:end;
          align-items:flex-end;
  border:none;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  list-style:none;
  margin:0;
  padding:0;
  position:relative; }
  .bp3-tab-list > *:not(:last-child){
    margin-right:20px; }

.bp3-tab{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  color:#182026;
  cursor:pointer;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  font-size:14px;
  line-height:30px;
  max-width:100%;
  position:relative;
  vertical-align:top; }
  .bp3-tab a{
    color:inherit;
    display:block;
    text-decoration:none; }
  .bp3-tab-indicator-wrapper ~ .bp3-tab{
    background-color:transparent !important;
    -webkit-box-shadow:none !important;
            box-shadow:none !important; }
  .bp3-tab[aria-disabled="true"]{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-tab[aria-selected="true"]{
    border-radius:0;
    -webkit-box-shadow:inset 0 -3px 0 #106ba3;
            box-shadow:inset 0 -3px 0 #106ba3; }
  .bp3-tab[aria-selected="true"], .bp3-tab:not([aria-disabled="true"]):hover{
    color:#106ba3; }
  .bp3-tab:focus{
    -moz-outline-radius:0; }
  .bp3-large > .bp3-tab{
    font-size:16px;
    line-height:40px; }

.bp3-tab-panel{
  margin-top:20px; }
  .bp3-tab-panel[aria-hidden="true"]{
    display:none; }

.bp3-tab-indicator-wrapper{
  left:0;
  pointer-events:none;
  position:absolute;
  top:0;
  -webkit-transform:translateX(0), translateY(0);
          transform:translateX(0), translateY(0);
  -webkit-transition:height, width, -webkit-transform;
  transition:height, width, -webkit-transform;
  transition:height, transform, width;
  transition:height, transform, width, -webkit-transform;
  -webkit-transition-duration:200ms;
          transition-duration:200ms;
  -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
          transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tab-indicator-wrapper .bp3-tab-indicator{
    background-color:#106ba3;
    bottom:0;
    height:3px;
    left:0;
    position:absolute;
    right:0; }
  .bp3-tab-indicator-wrapper.bp3-no-animation{
    -webkit-transition:none;
    transition:none; }

.bp3-dark .bp3-tab{
  color:#f5f8fa; }
  .bp3-dark .bp3-tab[aria-disabled="true"]{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tab[aria-selected="true"]{
    -webkit-box-shadow:inset 0 -3px 0 #48aff0;
            box-shadow:inset 0 -3px 0 #48aff0; }
  .bp3-dark .bp3-tab[aria-selected="true"], .bp3-dark .bp3-tab:not([aria-disabled="true"]):hover{
    color:#48aff0; }

.bp3-dark .bp3-tab-indicator{
  background-color:#48aff0; }

.bp3-flex-expander{
  -webkit-box-flex:1;
      -ms-flex:1 1;
          flex:1 1; }
.bp3-tag{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:#5c7080;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:none;
          box-shadow:none;
  color:#f5f8fa;
  font-size:12px;
  line-height:16px;
  max-width:100%;
  min-height:20px;
  min-width:20px;
  padding:2px 6px;
  position:relative; }
  .bp3-tag.bp3-interactive{
    cursor:pointer; }
    .bp3-tag.bp3-interactive:hover{
      background-color:rgba(92, 112, 128, 0.85); }
    .bp3-tag.bp3-interactive.bp3-active, .bp3-tag.bp3-interactive:active{
      background-color:rgba(92, 112, 128, 0.7); }
  .bp3-tag > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag::before,
  .bp3-tag > *{
    margin-right:4px; }
  .bp3-tag:empty::before,
  .bp3-tag > :last-child{
    margin-right:0; }
  .bp3-tag:focus{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:0;
    -moz-outline-radius:6px; }
  .bp3-tag.bp3-round{
    border-radius:30px;
    padding-left:8px;
    padding-right:8px; }
  .bp3-dark .bp3-tag{
    background-color:#bfccd6;
    color:#182026; }
    .bp3-dark .bp3-tag.bp3-interactive{
      cursor:pointer; }
      .bp3-dark .bp3-tag.bp3-interactive:hover{
        background-color:rgba(191, 204, 214, 0.85); }
      .bp3-dark .bp3-tag.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-interactive:active{
        background-color:rgba(191, 204, 214, 0.7); }
    .bp3-dark .bp3-tag > .bp3-icon, .bp3-dark .bp3-tag .bp3-icon-standard, .bp3-dark .bp3-tag .bp3-icon-large{
      fill:currentColor; }
  .bp3-tag > .bp3-icon, .bp3-tag .bp3-icon-standard, .bp3-tag .bp3-icon-large{
    fill:#ffffff; }
  .bp3-tag.bp3-large,
  .bp3-large .bp3-tag{
    font-size:14px;
    line-height:20px;
    min-height:30px;
    min-width:30px;
    padding:5px 10px; }
    .bp3-tag.bp3-large::before,
    .bp3-tag.bp3-large > *,
    .bp3-large .bp3-tag::before,
    .bp3-large .bp3-tag > *{
      margin-right:7px; }
    .bp3-tag.bp3-large:empty::before,
    .bp3-tag.bp3-large > :last-child,
    .bp3-large .bp3-tag:empty::before,
    .bp3-large .bp3-tag > :last-child{
      margin-right:0; }
    .bp3-tag.bp3-large.bp3-round,
    .bp3-large .bp3-tag.bp3-round{
      padding-left:12px;
      padding-right:12px; }
  .bp3-tag.bp3-intent-primary{
    background:#137cbd;
    color:#ffffff; }
    .bp3-tag.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.85); }
      .bp3-tag.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.7); }
  .bp3-tag.bp3-intent-success{
    background:#0f9960;
    color:#ffffff; }
    .bp3-tag.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.85); }
      .bp3-tag.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.7); }
  .bp3-tag.bp3-intent-warning{
    background:#d9822b;
    color:#ffffff; }
    .bp3-tag.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.85); }
      .bp3-tag.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.7); }
  .bp3-tag.bp3-intent-danger{
    background:#db3737;
    color:#ffffff; }
    .bp3-tag.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.85); }
      .bp3-tag.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.7); }
  .bp3-tag.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-tag.bp3-minimal > .bp3-icon, .bp3-tag.bp3-minimal .bp3-icon-standard, .bp3-tag.bp3-minimal .bp3-icon-large{
    fill:#5c7080; }
  .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
    background-color:rgba(138, 155, 168, 0.2);
    color:#182026; }
    .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
        background-color:rgba(92, 112, 128, 0.3); }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
        background-color:rgba(92, 112, 128, 0.4); }
    .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
      color:#f5f8fa; }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
          background-color:rgba(191, 204, 214, 0.3); }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
          background-color:rgba(191, 204, 214, 0.4); }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) > .bp3-icon, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-large{
        fill:#a7b6c2; }
  .bp3-tag.bp3-minimal.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15);
    color:#106ba3; }
    .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-primary > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-large{
      fill:#137cbd; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25);
      color:#48aff0; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
          background-color:rgba(19, 124, 189, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
          background-color:rgba(19, 124, 189, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15);
    color:#0d8050; }
    .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-success > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-large{
      fill:#0f9960; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25);
      color:#3dcc91; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
          background-color:rgba(15, 153, 96, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
          background-color:rgba(15, 153, 96, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15);
    color:#bf7326; }
    .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-warning > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-large{
      fill:#d9822b; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25);
      color:#ffb366; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
          background-color:rgba(217, 130, 43, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
          background-color:rgba(217, 130, 43, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15);
    color:#c23030; }
    .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-danger > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-large{
      fill:#db3737; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25);
      color:#ff7373; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
          background-color:rgba(219, 55, 55, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
          background-color:rgba(219, 55, 55, 0.45); }

.bp3-tag-remove{
  background:none;
  border:none;
  color:inherit;
  cursor:pointer;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin-bottom:-2px;
  margin-right:-6px !important;
  margin-top:-2px;
  opacity:0.5;
  padding:2px;
  padding-left:0; }
  .bp3-tag-remove:hover{
    background:none;
    opacity:0.8;
    text-decoration:none; }
  .bp3-tag-remove:active{
    opacity:1; }
  .bp3-tag-remove:empty::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    content:""; }
  .bp3-large .bp3-tag-remove{
    margin-right:-10px !important;
    padding:0 5px 0 0; }
    .bp3-large .bp3-tag-remove:empty::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1; }
.bp3-tag-input{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  cursor:text;
  height:auto;
  line-height:inherit;
  min-height:30px;
  padding-left:5px;
  padding-right:0; }
  .bp3-tag-input > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag-input > .bp3-tag-input-values{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag-input .bp3-tag-input-icon{
    color:#5c7080;
    margin-left:2px;
    margin-right:7px;
    margin-top:7px; }
  .bp3-tag-input .bp3-tag-input-values{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    -ms-flex-item-align:stretch;
        align-self:stretch;
    -ms-flex-wrap:wrap;
        flex-wrap:wrap;
    margin-right:7px;
    margin-top:5px;
    min-width:0; }
    .bp3-tag-input .bp3-tag-input-values > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-tag-input .bp3-tag-input-values > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-tag-input .bp3-tag-input-values::before,
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-right:5px; }
    .bp3-tag-input .bp3-tag-input-values:empty::before,
    .bp3-tag-input .bp3-tag-input-values > :last-child{
      margin-right:0; }
    .bp3-tag-input .bp3-tag-input-values:first-child .bp3-input-ghost:first-child{
      padding-left:5px; }
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-bottom:5px; }
  .bp3-tag-input .bp3-tag{
    overflow-wrap:break-word; }
    .bp3-tag-input .bp3-tag.bp3-active{
      outline:rgba(19, 124, 189, 0.6) auto 2px;
      outline-offset:0;
      -moz-outline-radius:6px; }
  .bp3-tag-input .bp3-input-ghost{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:20px;
    width:80px; }
    .bp3-tag-input .bp3-input-ghost:disabled, .bp3-tag-input .bp3-input-ghost.bp3-disabled{
      cursor:not-allowed; }
  .bp3-tag-input .bp3-button,
  .bp3-tag-input .bp3-spinner{
    margin:3px;
    margin-left:0; }
  .bp3-tag-input .bp3-button{
    min-height:24px;
    min-width:24px;
    padding:0 7px; }
  .bp3-tag-input.bp3-large{
    height:auto;
    min-height:40px; }
    .bp3-tag-input.bp3-large::before,
    .bp3-tag-input.bp3-large > *{
      margin-right:10px; }
    .bp3-tag-input.bp3-large:empty::before,
    .bp3-tag-input.bp3-large > :last-child{
      margin-right:0; }
    .bp3-tag-input.bp3-large .bp3-tag-input-icon{
      margin-left:5px;
      margin-top:10px; }
    .bp3-tag-input.bp3-large .bp3-input-ghost{
      line-height:30px; }
    .bp3-tag-input.bp3-large .bp3-button{
      min-height:30px;
      min-width:30px;
      padding:5px 10px;
      margin:5px;
      margin-left:0; }
    .bp3-tag-input.bp3-large .bp3-spinner{
      margin:8px;
      margin-left:0; }
  .bp3-tag-input.bp3-active{
    background-color:#ffffff;
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-tag-input .bp3-tag-input-icon, .bp3-tag-input.bp3-dark .bp3-tag-input-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-tag-input .bp3-input-ghost, .bp3-tag-input.bp3-dark .bp3-input-ghost{
    color:#f5f8fa; }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-webkit-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-moz-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost:-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::placeholder{
      color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tag-input.bp3-active, .bp3-tag-input.bp3-dark.bp3-active{
    background-color:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-primary, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-success, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-warning, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-danger, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-input-ghost{
  background:none;
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0; }
  .bp3-input-ghost::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost:focus{
    outline:none !important; }
.bp3-toast{
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin:20px 0 0;
  max-width:500px;
  min-width:300px;
  pointer-events:all;
  position:relative !important; }
  .bp3-toast.bp3-toast-enter, .bp3-toast.bp3-toast-appear{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active, .bp3-toast.bp3-toast-appear-active{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-toast.bp3-toast-enter ~ .bp3-toast, .bp3-toast.bp3-toast-appear ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active ~ .bp3-toast, .bp3-toast.bp3-toast-appear-active ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-toast.bp3-toast-exit{
    opacity:1;
    -webkit-filter:blur(0);
            filter:blur(0); }
  .bp3-toast.bp3-toast-exit-active{
    opacity:0;
    -webkit-filter:blur(10px);
            filter:blur(10px);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:opacity, filter;
    transition-property:opacity, filter, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-toast.bp3-toast-exit ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0); }
  .bp3-toast.bp3-toast-exit-active ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px);
    -webkit-transition-delay:50ms;
            transition-delay:50ms;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-toast .bp3-button-group{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    padding:5px;
    padding-left:0; }
  .bp3-toast > .bp3-icon{
    color:#5c7080;
    margin:12px;
    margin-right:0; }
  .bp3-toast.bp3-dark,
  .bp3-dark .bp3-toast{
    background-color:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-toast.bp3-dark > .bp3-icon,
    .bp3-dark .bp3-toast > .bp3-icon{
      color:#a7b6c2; }
  .bp3-toast[class*="bp3-intent-"] a{
    color:rgba(255, 255, 255, 0.7); }
    .bp3-toast[class*="bp3-intent-"] a:hover{
      color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] > .bp3-icon{
    color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button, .bp3-toast[class*="bp3-intent-"] .bp3-button::before,
  .bp3-toast[class*="bp3-intent-"] .bp3-button .bp3-icon, .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    color:rgba(255, 255, 255, 0.7) !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:focus{
    outline-color:rgba(255, 255, 255, 0.5); }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:hover{
    background-color:rgba(255, 255, 255, 0.15) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    background-color:rgba(255, 255, 255, 0.3) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button::after{
    background:rgba(255, 255, 255, 0.3) !important; }
  .bp3-toast.bp3-intent-primary{
    background-color:#137cbd;
    color:#ffffff; }
  .bp3-toast.bp3-intent-success{
    background-color:#0f9960;
    color:#ffffff; }
  .bp3-toast.bp3-intent-warning{
    background-color:#d9822b;
    color:#ffffff; }
  .bp3-toast.bp3-intent-danger{
    background-color:#db3737;
    color:#ffffff; }

.bp3-toast-message{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  padding:11px;
  word-break:break-word; }

.bp3-toast-container{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box !important;
  display:-ms-flexbox !important;
  display:flex !important;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  left:0;
  overflow:hidden;
  padding:0 20px 20px;
  pointer-events:none;
  right:0;
  z-index:40; }
  .bp3-toast-container.bp3-toast-container-in-portal{
    position:fixed; }
  .bp3-toast-container.bp3-toast-container-inline{
    position:absolute; }
  .bp3-toast-container.bp3-toast-container-top{
    top:0; }
  .bp3-toast-container.bp3-toast-container-bottom{
    bottom:0;
    -webkit-box-orient:vertical;
    -webkit-box-direction:reverse;
        -ms-flex-direction:column-reverse;
            flex-direction:column-reverse;
    top:auto; }
  .bp3-toast-container.bp3-toast-container-left{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start; }
  .bp3-toast-container.bp3-toast-container-right{
    -webkit-box-align:end;
        -ms-flex-align:end;
            align-items:flex-end; }

.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active) ~ .bp3-toast, .bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active) ~ .bp3-toast,
.bp3-toast-container-bottom .bp3-toast.bp3-toast-exit-active ~ .bp3-toast,
.bp3-toast-container-bottom .bp3-toast.bp3-toast-leave-active ~ .bp3-toast{
  -webkit-transform:translateY(60px);
          transform:translateY(60px); }
.bp3-tooltip{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1); }
  .bp3-tooltip .bp3-popover-arrow{
    height:22px;
    position:absolute;
    width:22px; }
    .bp3-tooltip .bp3-popover-arrow::before{
      height:14px;
      margin:4px;
      width:14px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip{
    margin-bottom:11px;
    margin-top:-11px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
      bottom:-8px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip{
    margin-left:11px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
      left:-8px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip{
    margin-top:11px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
      top:-8px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip{
    margin-left:-11px;
    margin-right:11px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
      right:-8px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-tooltip > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-tooltip > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
    top:-0.22183px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
    right:-0.22183px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
    left:-0.22183px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
    bottom:-0.22183px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-tooltip .bp3-popover-content{
    background:#394b59;
    color:#f5f8fa; }
  .bp3-tooltip .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-tooltip .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-tooltip .bp3-popover-arrow-fill{
    fill:#394b59; }
  .bp3-popover-enter > .bp3-tooltip, .bp3-popover-appear > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8); }
  .bp3-popover-enter-active > .bp3-tooltip, .bp3-popover-appear-active > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-popover-exit > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tooltip .bp3-popover-content{
    padding:10px 12px; }
  .bp3-tooltip.bp3-dark,
  .bp3-dark .bp3-tooltip{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-tooltip .bp3-popover-content{
      background:#e1e8ed;
      color:#394b59; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-fill{
      fill:#e1e8ed; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-content{
    background:#137cbd;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-arrow-fill{
    fill:#137cbd; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-content{
    background:#0f9960;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-arrow-fill{
    fill:#0f9960; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-content{
    background:#d9822b;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-arrow-fill{
    fill:#d9822b; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-content{
    background:#db3737;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-arrow-fill{
    fill:#db3737; }

.bp3-tooltip-indicator{
  border-bottom:dotted 1px;
  cursor:help; }
.bp3-tree .bp3-icon, .bp3-tree .bp3-icon-standard, .bp3-tree .bp3-icon-large{
  color:#5c7080; }
  .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-tree .bp3-icon.bp3-intent-success, .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-tree-node-list{
  list-style:none;
  margin:0;
  padding-left:0; }

.bp3-tree-root{
  background-color:transparent;
  cursor:default;
  padding-left:0;
  position:relative; }

.bp3-tree-node-content-0{
  padding-left:0px; }

.bp3-tree-node-content-1{
  padding-left:23px; }

.bp3-tree-node-content-2{
  padding-left:46px; }

.bp3-tree-node-content-3{
  padding-left:69px; }

.bp3-tree-node-content-4{
  padding-left:92px; }

.bp3-tree-node-content-5{
  padding-left:115px; }

.bp3-tree-node-content-6{
  padding-left:138px; }

.bp3-tree-node-content-7{
  padding-left:161px; }

.bp3-tree-node-content-8{
  padding-left:184px; }

.bp3-tree-node-content-9{
  padding-left:207px; }

.bp3-tree-node-content-10{
  padding-left:230px; }

.bp3-tree-node-content-11{
  padding-left:253px; }

.bp3-tree-node-content-12{
  padding-left:276px; }

.bp3-tree-node-content-13{
  padding-left:299px; }

.bp3-tree-node-content-14{
  padding-left:322px; }

.bp3-tree-node-content-15{
  padding-left:345px; }

.bp3-tree-node-content-16{
  padding-left:368px; }

.bp3-tree-node-content-17{
  padding-left:391px; }

.bp3-tree-node-content-18{
  padding-left:414px; }

.bp3-tree-node-content-19{
  padding-left:437px; }

.bp3-tree-node-content-20{
  padding-left:460px; }

.bp3-tree-node-content{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:30px;
  padding-right:5px;
  width:100%; }
  .bp3-tree-node-content:hover{
    background-color:rgba(191, 204, 214, 0.4); }

.bp3-tree-node-caret,
.bp3-tree-node-caret-none{
  min-width:30px; }

.bp3-tree-node-caret{
  color:#5c7080;
  cursor:pointer;
  padding:7px;
  -webkit-transform:rotate(0deg);
          transform:rotate(0deg);
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tree-node-caret:hover{
    color:#182026; }
  .bp3-dark .bp3-tree-node-caret{
    color:#a7b6c2; }
    .bp3-dark .bp3-tree-node-caret:hover{
      color:#f5f8fa; }
  .bp3-tree-node-caret.bp3-tree-node-caret-open{
    -webkit-transform:rotate(90deg);
            transform:rotate(90deg); }
  .bp3-tree-node-caret.bp3-icon-standard::before{
    content:""; }

.bp3-tree-node-icon{
  margin-right:7px;
  position:relative; }

.bp3-tree-node-label{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  position:relative;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-label span{
    display:inline; }

.bp3-tree-node-secondary-label{
  padding:0 5px;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-secondary-label .bp3-popover-wrapper,
  .bp3-tree-node-secondary-label .bp3-popover-target{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }

.bp3-tree-node.bp3-disabled .bp3-tree-node-content{
  background-color:inherit;
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-tree-node.bp3-disabled .bp3-tree-node-caret,
.bp3-tree-node.bp3-disabled .bp3-tree-node-icon{
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content,
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-standard, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-large{
    color:#ffffff; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret::before{
    color:rgba(255, 255, 255, 0.7); }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret:hover::before{
    color:#ffffff; }

.bp3-dark .bp3-tree-node-content:hover{
  background-color:rgba(92, 112, 128, 0.3); }

.bp3-dark .bp3-tree .bp3-icon, .bp3-dark .bp3-tree .bp3-icon-standard, .bp3-dark .bp3-tree .bp3-icon-large{
  color:#a7b6c2; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-dark .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
.bp3-omnibar{
  -webkit-filter:blur(0);
          filter:blur(0);
  opacity:1;
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  left:calc(50% - 250px);
  top:20vh;
  width:500px;
  z-index:21; }
  .bp3-omnibar.bp3-overlay-enter, .bp3-omnibar.bp3-overlay-appear{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2; }
  .bp3-omnibar.bp3-overlay-enter-active, .bp3-omnibar.bp3-overlay-appear-active{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-omnibar.bp3-overlay-exit{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1; }
  .bp3-omnibar.bp3-overlay-exit-active{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-omnibar .bp3-input{
    background-color:transparent;
    border-radius:0; }
    .bp3-omnibar .bp3-input, .bp3-omnibar .bp3-input:focus{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-omnibar .bp3-menu{
    background-color:transparent;
    border-radius:0;
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
    max-height:calc(60vh - 40px);
    overflow:auto; }
    .bp3-omnibar .bp3-menu:empty{
      display:none; }
  .bp3-dark .bp3-omnibar, .bp3-omnibar.bp3-dark{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

.bp3-omnibar-overlay .bp3-overlay-backdrop{
  background-color:rgba(16, 22, 26, 0.2); }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }

.bp3-multi-select{
  min-width:150px; }

.bp3-multi-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto; }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

/* Icons urls */

:root {
  --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yMCA4aC0yLjgxYy0uNDUtLjc4LTEuMDctMS40NS0xLjgyLTEuOTZMMTcgNC40MSAxNS41OSAzbC0yLjE3IDIuMTdDMTIuOTYgNS4wNiAxMi40OSA1IDEyIDVjLS40OSAwLS45Ni4wNi0xLjQxLjE3TDguNDEgMyA3IDQuNDFsMS42MiAxLjYzQzcuODggNi41NSA3LjI2IDcuMjIgNi44MSA4SDR2MmgyLjA5Yy0uMDUuMzMtLjA5LjY2LS4wOSAxdjFINHYyaDJ2MWMwIC4zNC4wNC42Ny4wOSAxSDR2MmgyLjgxYzEuMDQgMS43OSAyLjk3IDMgNS4xOSAzczQuMTUtMS4yMSA1LjE5LTNIMjB2LTJoLTIuMDljLjA1LS4zMy4wOS0uNjYuMDktMXYtMWgydi0yaC0ydi0xYzAtLjM0LS4wNC0uNjctLjA5LTFIMjBWOHptLTYgOGgtNHYtMmg0djJ6bTAtNGgtNHYtMmg0djJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik05IDE2LjE3TDQuODMgMTJsLTEuNDIgMS40MUw5IDE5IDIxIDdsLTEuNDEtMS40MXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-code: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTExLjQgMTguNkw2LjggMTRMMTEuNCA5LjRMMTAgOEw0IDE0TDEwIDIwTDExLjQgMTguNlpNMTYuNiAxOC42TDIxLjIgMTRMMTYuNiA5LjRMMTggOEwyNCAxNEwxOCAyMEwxNi42IDE4LjZWMTguNloiLz4KCTwvZz4KPC9zdmc+Cg==);
  --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1pY29uLWJyYW5kMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNmZmYiPgogICAgPHBhdGggZD0iTTEwNSAxMjcuM2g0MHYxMi44aC00MHpNNTEuMSA3N0w3NCA5OS45bC0yMy4zIDIzLjMgMTAuNSAxMC41IDIzLjMtMjMuM0w5NSA5OS45IDg0LjUgODkuNCA2MS42IDY2LjV6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-copyright: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGVuYWJsZS1iYWNrZ3JvdW5kPSJuZXcgMCAwIDI0IDI0IiBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCI+CiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0xMS44OCw5LjE0YzEuMjgsMC4wNiwxLjYxLDEuMTUsMS42MywxLjY2aDEuNzljLTAuMDgtMS45OC0xLjQ5LTMuMTktMy40NS0zLjE5QzkuNjQsNy42MSw4LDksOCwxMi4xNCBjMCwxLjk0LDAuOTMsNC4yNCwzLjg0LDQuMjRjMi4yMiwwLDMuNDEtMS42NSwzLjQ0LTIuOTVoLTEuNzljLTAuMDMsMC41OS0wLjQ1LDEuMzgtMS42MywxLjQ0QzEwLjU1LDE0LjgzLDEwLDEzLjgxLDEwLDEyLjE0IEMxMCw5LjI1LDExLjI4LDkuMTYsMTEuODgsOS4xNHogTTEyLDJDNi40OCwyLDIsNi40OCwyLDEyczQuNDgsMTAsMTAsMTBzMTAtNC40OCwxMC0xMFMxNy41MiwyLDEyLDJ6IE0xMiwyMGMtNC40MSwwLTgtMy41OS04LTggczMuNTktOCw4LThzOCwzLjU5LDgsOFMxNi40MSwyMCwxMiwyMHoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
  --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
  --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNGOUE4MjUiPgogICAgPHBhdGggZD0iTTIwLjIgMTEuOGMtMS42IDAtMS43LjUtMS43IDEgMCAuNC4xLjkuMSAxLjMuMS41LjEuOS4xIDEuMyAwIDEuNy0xLjQgMi4zLTMuNSAyLjNoLS45di0xLjloLjVjMS4xIDAgMS40IDAgMS40LS44IDAtLjMgMC0uNi0uMS0xIDAtLjQtLjEtLjgtLjEtMS4yIDAtMS4zIDAtMS44IDEuMy0yLTEuMy0uMi0xLjMtLjctMS4zLTIgMC0uNC4xLS44LjEtMS4yLjEtLjQuMS0uNy4xLTEgMC0uOC0uNC0uNy0xLjQtLjhoLS41VjQuMWguOWMyLjIgMCAzLjUuNyAzLjUgMi4zIDAgLjQtLjEuOS0uMSAxLjMtLjEuNS0uMS45LS4xIDEuMyAwIC41LjIgMSAxLjcgMXYxLjh6TTEuOCAxMC4xYzEuNiAwIDEuNy0uNSAxLjctMSAwLS40LS4xLS45LS4xLTEuMy0uMS0uNS0uMS0uOS0uMS0xLjMgMC0xLjYgMS40LTIuMyAzLjUtMi4zaC45djEuOWgtLjVjLTEgMC0xLjQgMC0xLjQuOCAwIC4zIDAgLjYuMSAxIDAgLjIuMS42LjEgMSAwIDEuMyAwIDEuOC0xLjMgMkM2IDExLjIgNiAxMS43IDYgMTNjMCAuNC0uMS44LS4xIDEuMi0uMS4zLS4xLjctLjEgMSAwIC44LjMuOCAxLjQuOGguNXYxLjloLS45Yy0yLjEgMC0zLjUtLjYtMy41LTIuMyAwLS40LjEtLjkuMS0xLjMuMS0uNS4xLS45LjEtMS4zIDAtLjUtLjItMS0xLjctMXYtMS45eiIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSIxMy44IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY3g9IjExIiBjeT0iOC4yIiByPSIyLjEiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-julia: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDMyNSAzMDAiPgogIDxnIGNsYXNzPSJqcC1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjY2IzYzMzIj4KICAgIDxwYXRoIGQ9Ik0gMTUwLjg5ODQzOCAyMjUgQyAxNTAuODk4NDM4IDI2Ni40MjE4NzUgMTE3LjMyMDMxMiAzMDAgNzUuODk4NDM4IDMwMCBDIDM0LjQ3NjU2MiAzMDAgMC44OTg0MzggMjY2LjQyMTg3NSAwLjg5ODQzOCAyMjUgQyAwLjg5ODQzOCAxODMuNTc4MTI1IDM0LjQ3NjU2MiAxNTAgNzUuODk4NDM4IDE1MCBDIDExNy4zMjAzMTIgMTUwIDE1MC44OTg0MzggMTgzLjU3ODEyNSAxNTAuODk4NDM4IDIyNSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzM4OTgyNiI+CiAgICA8cGF0aCBkPSJNIDIzNy41IDc1IEMgMjM3LjUgMTE2LjQyMTg3NSAyMDMuOTIxODc1IDE1MCAxNjIuNSAxNTAgQyAxMjEuMDc4MTI1IDE1MCA4Ny41IDExNi40MjE4NzUgODcuNSA3NSBDIDg3LjUgMzMuNTc4MTI1IDEyMS4wNzgxMjUgMCAxNjIuNSAwIEMgMjAzLjkyMTg3NSAwIDIzNy41IDMzLjU3ODEyNSAyMzcuNSA3NSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzk1NThiMiI+CiAgICA8cGF0aCBkPSJNIDMyNC4xMDE1NjIgMjI1IEMgMzI0LjEwMTU2MiAyNjYuNDIxODc1IDI5MC41MjM0MzggMzAwIDI0OS4xMDE1NjIgMzAwIEMgMjA3LjY3OTY4OCAzMDAgMTc0LjEwMTU2MiAyNjYuNDIxODc1IDE3NC4xMDE1NjIgMjI1IEMgMTc0LjEwMTU2MiAxODMuNTc4MTI1IDIwNy42Nzk2ODggMTUwIDI0OS4xMDE1NjIgMTUwIEMgMjkwLjUyMzQzOCAxNTAgMzI0LjEwMTU2MiAxODMuNTc4MTI1IDMyNC4xMDE1NjIgMjI1Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgPGcgY2xhc3M9ImpwLWljb24td2FybjAiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
  --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
  --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
  --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
  --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4=);
  --jp-icon-listings-info: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MC45NzggNTAuOTc4IiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA1MC45NzggNTAuOTc4OyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+Cgk8Zz4KCQk8cGF0aCBzdHlsZT0iZmlsbDojMDEwMDAyOyIgZD0iTTQzLjUyLDcuNDU4QzM4LjcxMSwyLjY0OCwzMi4zMDcsMCwyNS40ODksMEMxOC42NywwLDEyLjI2NiwyLjY0OCw3LjQ1OCw3LjQ1OAoJCQljLTkuOTQzLDkuOTQxLTkuOTQzLDI2LjExOSwwLDM2LjA2MmM0LjgwOSw0LjgwOSwxMS4yMTIsNy40NTYsMTguMDMxLDcuNDU4YzAsMCwwLjAwMSwwLDAuMDAyLDAKCQkJYzYuODE2LDAsMTMuMjIxLTIuNjQ4LDE4LjAyOS03LjQ1OGM0LjgwOS00LjgwOSw3LjQ1Ny0xMS4yMTIsNy40NTctMTguMDNDNTAuOTc3LDE4LjY3LDQ4LjMyOCwxMi4yNjYsNDMuNTIsNy40NTh6CgkJCSBNNDIuMTA2LDQyLjEwNWMtNC40MzIsNC40MzEtMTAuMzMyLDYuODcyLTE2LjYxNSw2Ljg3MmgtMC4wMDJjLTYuMjg1LTAuMDAxLTEyLjE4Ny0yLjQ0MS0xNi42MTctNi44NzIKCQkJYy05LjE2Mi05LjE2My05LjE2Mi0yNC4wNzEsMC0zMy4yMzNDMTMuMzAzLDQuNDQsMTkuMjA0LDIsMjUuNDg5LDJjNi4yODQsMCwxMi4xODYsMi40NCwxNi42MTcsNi44NzIKCQkJYzQuNDMxLDQuNDMxLDYuODcxLDEwLjMzMiw2Ljg3MSwxNi42MTdDNDguOTc3LDMxLjc3Miw0Ni41MzYsMzcuNjc1LDQyLjEwNiw0Mi4xMDV6Ii8+CgkJPHBhdGggc3R5bGU9ImZpbGw6IzAxMDAwMjsiIGQ9Ik0yMy41NzgsMzIuMjE4Yy0wLjAyMy0xLjczNCwwLjE0My0zLjA1OSwwLjQ5Ni0zLjk3MmMwLjM1My0wLjkxMywxLjExLTEuOTk3LDIuMjcyLTMuMjUzCgkJCWMwLjQ2OC0wLjUzNiwwLjkyMy0xLjA2MiwxLjM2Ny0xLjU3NWMwLjYyNi0wLjc1MywxLjEwNC0xLjQ3OCwxLjQzNi0yLjE3NWMwLjMzMS0wLjcwNywwLjQ5NS0xLjU0MSwwLjQ5NS0yLjUKCQkJYzAtMS4wOTYtMC4yNi0yLjA4OC0wLjc3OS0yLjk3OWMtMC41NjUtMC44NzktMS41MDEtMS4zMzYtMi44MDYtMS4zNjljLTEuODAyLDAuMDU3LTIuOTg1LDAuNjY3LTMuNTUsMS44MzIKCQkJYy0wLjMwMSwwLjUzNS0wLjUwMywxLjE0MS0wLjYwNywxLjgxNGMtMC4xMzksMC43MDctMC4yMDcsMS40MzItMC4yMDcsMi4xNzRoLTIuOTM3Yy0wLjA5MS0yLjIwOCwwLjQwNy00LjExNCwxLjQ5My01LjcxOQoJCQljMS4wNjItMS42NCwyLjg1NS0yLjQ4MSw1LjM3OC0yLjUyN2MyLjE2LDAuMDIzLDMuODc0LDAuNjA4LDUuMTQxLDEuNzU4YzEuMjc4LDEuMTYsMS45MjksMi43NjQsMS45NSw0LjgxMQoJCQljMCwxLjE0Mi0wLjEzNywyLjExMS0wLjQxLDIuOTExYy0wLjMwOSwwLjg0NS0wLjczMSwxLjU5My0xLjI2OCwyLjI0M2MtMC40OTIsMC42NS0xLjA2OCwxLjMxOC0xLjczLDIuMDAyCgkJCWMtMC42NSwwLjY5Ny0xLjMxMywxLjQ3OS0xLjk4NywyLjM0NmMtMC4yMzksMC4zNzctMC40MjksMC43NzctMC41NjUsMS4xOTljLTAuMTYsMC45NTktMC4yMTcsMS45NTEtMC4xNzEsMi45NzkKCQkJQzI2LjU4OSwzMi4yMTgsMjMuNTc4LDMyLjIxOCwyMy41NzgsMzIuMjE4eiBNMjMuNTc4LDM4LjIydi0zLjQ4NGgzLjA3NnYzLjQ4NEgyMy41Nzh6Ii8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
  --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-numbering: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTQgMTlINlYxOS41SDVWMjAuNUg2VjIxSDRWMjJIN1YxOEg0VjE5Wk01IDEwSDZWNkg0VjdINVYxMFpNNCAxM0g1LjhMNCAxNS4xVjE2SDdWMTVINS4yTDcgMTIuOVYxMkg0VjEzWk05IDdWOUgyM1Y3SDlaTTkgMjFIMjNWMTlIOVYyMVpNOSAxNUgyM1YxM0g5VjE1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-offline-bolt: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDIuMDJjLTUuNTEgMC05Ljk4IDQuNDctOS45OCA5Ljk4czQuNDcgOS45OCA5Ljk4IDkuOTggOS45OC00LjQ3IDkuOTgtOS45OFMxNy41MSAyLjAyIDEyIDIuMDJ6TTExLjQ4IDIwdi02LjI2SDhMMTMgNHY2LjI2aDMuMzVMMTEuNDggMjB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-pdf: url(data:image/svg+xml;base64,PHN2ZwogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyMiAyMiIgd2lkdGg9IjE2Ij4KICAgIDxwYXRoIHRyYW5zZm9ybT0icm90YXRlKDQ1KSIgY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0ZGMkEyQSIKICAgICAgIGQ9Im0gMjIuMzQ0MzY5LC0zLjAxNjM2NDIgaCA1LjYzODYwNCB2IDEuNTc5MjQzMyBoIC0zLjU0OTIyNyB2IDEuNTA4NjkyOTkgaCAzLjMzNzU3NiBWIDEuNjUwODE1NCBoIC0zLjMzNzU3NiB2IDMuNDM1MjYxMyBoIC0yLjA4OTM3NyB6IG0gLTcuMTM2NDQ0LDEuNTc5MjQzMyB2IDQuOTQzOTU0MyBoIDAuNzQ4OTIgcSAxLjI4MDc2MSwwIDEuOTUzNzAzLC0wLjYzNDk1MzUgMC42NzgzNjksLTAuNjM0OTUzNSAwLjY3ODM2OSwtMS44NDUxNjQxIDAsLTEuMjA0NzgzNTUgLTAuNjcyOTQyLC0xLjgzNDMxMDExIC0wLjY3Mjk0MiwtMC42Mjk1MjY1OSAtMS45NTkxMywtMC42Mjk1MjY1OSB6IG0gLTIuMDg5Mzc3LC0xLjU3OTI0MzMgaCAyLjIwMzM0MyBxIDEuODQ1MTY0LDAgMi43NDYwMzksMC4yNjU5MjA3IDAuOTA2MzAxLDAuMjYwNDkzNyAxLjU1MjEwOCwwLjg5MDAyMDMgMC41Njk4MywwLjU0ODEyMjMgMC44NDY2MDUsMS4yNjQ0ODAwNiAwLjI3Njc3NCwwLjcxNjM1NzgxIDAuMjc2Nzc0LDEuNjIyNjU4OTQgMCwwLjkxNzE1NTEgLTAuMjc2Nzc0LDEuNjM4OTM5OSAtMC4yNzY3NzUsMC43MTYzNTc4IC0wLjg0NjYwNSwxLjI2NDQ4IC0wLjY1MTIzNCwwLjYyOTUyNjYgLTEuNTYyOTYyLDAuODk1NDQ3MyAtMC45MTE3MjgsMC4yNjA0OTM3IC0yLjczNTE4NSwwLjI2MDQ5MzcgaCAtMi4yMDMzNDMgeiBtIC04LjE0NTg1NjUsMCBoIDMuNDY3ODIzIHEgMS41NDY2ODE2LDAgMi4zNzE1Nzg1LDAuNjg5MjIzIDAuODMwMzI0LDAuNjgzNzk2MSAwLjgzMDMyNCwxLjk1MzcwMzE0IDAsMS4yNzUzMzM5NyAtMC44MzAzMjQsMS45NjQ1NTcwNiBRIDkuOTg3MTk2MSwyLjI3NDkxNSA4LjQ0MDUxNDUsMi4yNzQ5MTUgSCA3LjA2MjA2ODQgViA1LjA4NjA3NjcgSCA0Ljk3MjY5MTUgWiBtIDIuMDg5Mzc2OSwxLjUxNDExOTkgdiAyLjI2MzAzOTQzIGggMS4xNTU5NDEgcSAwLjYwNzgxODgsMCAwLjkzODg2MjksLTAuMjkzMDU1NDcgMC4zMzEwNDQxLC0wLjI5ODQ4MjQxIDAuMzMxMDQ0MSwtMC44NDExNzc3MiAwLC0wLjU0MjY5NTMxIC0wLjMzMTA0NDEsLTAuODM1NzUwNzQgLTAuMzMxMDQ0MSwtMC4yOTMwNTU1IC0wLjkzODg2MjksLTAuMjkzMDU1NSB6IgovPgo8L3N2Zz4K);
  --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMEQ0N0ExIj4KICAgIDxwYXRoIGQ9Ik0xMS4xIDYuOVY1LjhINi45YzAtLjUgMC0xLjMuMi0xLjYuNC0uNy44LTEuMSAxLjctMS40IDEuNy0uMyAyLjUtLjMgMy45LS4xIDEgLjEgMS45LjkgMS45IDEuOXY0LjJjMCAuNS0uOSAxLjYtMiAxLjZIOC44Yy0xLjUgMC0yLjQgMS40LTIuNCAyLjh2Mi4ySDQuN0MzLjUgMTUuMSAzIDE0IDMgMTMuMVY5Yy0uMS0xIC42LTIgMS44LTIgMS41LS4xIDYuMy0uMSA2LjMtLjF6Ii8+CiAgICA8cGF0aCBkPSJNMTAuOSAxNS4xdjEuMWg0LjJjMCAuNSAwIDEuMy0uMiAxLjYtLjQuNy0uOCAxLjEtMS43IDEuNC0xLjcuMy0yLjUuMy0zLjkuMS0xLS4xLTEuOS0uOS0xLjktMS45di00LjJjMC0uNS45LTEuNiAyLTEuNmgzLjhjMS41IDAgMi40LTEuNCAyLjQtMi44VjYuNmgxLjdDMTguNSA2LjkgMTkgOCAxOSA4LjlWMTNjMCAxLS43IDIuMS0xLjkgMi4xaC02LjJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
  --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-redo: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIi8+PHBhdGggZD0iTTE4LjQgMTAuNkMxNi41NSA4Ljk5IDE0LjE1IDggMTEuNSA4Yy00LjY1IDAtOC41OCAzLjAzLTkuOTYgNy4yMkwzLjkgMTZjMS4wNS0zLjE5IDQuMDUtNS41IDcuNi01LjUgMS45NSAwIDMuNzMuNzIgNS4xMiAxLjg4TDEzIDE2aDlWN2wtMy42IDMuNnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
  --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-table-rows: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMSw4SDNWNGgxOFY4eiBNMjEsMTBIM3Y0aDE4VjEweiBNMjEsMTZIM3Y0aDE4VjE2eiIvPgogICAgPC9nPgo8L3N2Zz4=);
  --jp-icon-tag: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCA0MyAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTI4LjgzMzIgMTIuMzM0TDMyLjk5OTggMTYuNTAwN0wzNy4xNjY1IDEyLjMzNEgyOC44MzMyWiIvPgoJCTxwYXRoIGQ9Ik0xNi4yMDk1IDIxLjYxMDRDMTUuNjg3MyAyMi4xMjk5IDE0Ljg0NDMgMjIuMTI5OSAxNC4zMjQ4IDIxLjYxMDRMNi45ODI5IDE0LjcyNDVDNi41NzI0IDE0LjMzOTQgNi4wODMxMyAxMy42MDk4IDYuMDQ3ODYgMTMuMDQ4MkM1Ljk1MzQ3IDExLjUyODggNi4wMjAwMiA4LjYxOTQ0IDYuMDY2MjEgNy4wNzY5NUM2LjA4MjgxIDYuNTE0NzcgNi41NTU0OCA2LjA0MzQ3IDcuMTE4MDQgNi4wMzA1NUM5LjA4ODYzIDUuOTg0NzMgMTMuMjYzOCA1LjkzNTc5IDEzLjY1MTggNi4zMjQyNUwyMS43MzY5IDEzLjYzOUMyMi4yNTYgMTQuMTU4NSAyMS43ODUxIDE1LjQ3MjQgMjEuMjYyIDE1Ljk5NDZMMTYuMjA5NSAyMS42MTA0Wk05Ljc3NTg1IDguMjY1QzkuMzM1NTEgNy44MjU2NiA4LjYyMzUxIDcuODI1NjYgOC4xODI4IDguMjY1QzcuNzQzNDYgOC43MDU3MSA3Ljc0MzQ2IDkuNDE3MzMgOC4xODI4IDkuODU2NjdDOC42MjM4MiAxMC4yOTY0IDkuMzM1ODIgMTAuMjk2NCA5Ljc3NTg1IDkuODU2NjdDMTAuMjE1NiA5LjQxNzMzIDEwLjIxNTYgOC43MDUzMyA5Ljc3NTg1IDguMjY1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMikiIGZpbGw9IiMzMzMzMzMiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uLWFjY2VudDIganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGQ9Ik01LjA1NjY0IDguNzYxNzJDNS4wNTY2NCA4LjU5NzY2IDUuMDMxMjUgOC40NTMxMiA0Ljk4MDQ3IDguMzI4MTJDNC45MzM1OSA4LjE5OTIyIDQuODU1NDcgOC4wODIwMyA0Ljc0NjA5IDcuOTc2NTZDNC42NDA2MiA3Ljg3MTA5IDQuNSA3Ljc3NTM5IDQuMzI0MjIgNy42ODk0NUM0LjE1MjM0IDcuNTk5NjEgMy45NDMzNiA3LjUxMTcyIDMuNjk3MjcgNy40MjU3OEMzLjMwMjczIDcuMjg1MTYgMi45NDMzNiA3LjEzNjcyIDIuNjE5MTQgNi45ODA0N0MyLjI5NDkyIDYuODI0MjIgMi4wMTc1OCA2LjY0MjU4IDEuNzg3MTEgNi40MzU1NUMxLjU2MDU1IDYuMjI4NTIgMS4zODQ3NyA1Ljk4ODI4IDEuMjU5NzcgNS43MTQ4NEMxLjEzNDc3IDUuNDM3NSAxLjA3MjI3IDUuMTA5MzggMS4wNzIyNyA0LjczMDQ3QzEuMDcyMjcgNC4zOTg0NCAxLjEyODkxIDQuMDk1NyAxLjI0MjE5IDMuODIyMjdDMS4zNTU0NyAzLjU0NDkyIDEuNTE1NjIgMy4zMDQ2OSAxLjcyMjY2IDMuMTAxNTZDMS45Mjk2OSAyLjg5ODQ0IDIuMTc5NjkgMi43MzQzNyAyLjQ3MjY2IDIuNjA5MzhDMi43NjU2MiAyLjQ4NDM4IDMuMDkxOCAyLjQwNDMgMy40NTExNyAyLjM2OTE0VjEuMTA5MzhINC4zODg2N1YyLjM4MDg2QzQuNzQwMjMgMi40Mjc3MyA1LjA1NjY0IDIuNTIzNDQgNS4zMzc4OSAyLjY2Nzk3QzUuNjE5MTQgMi44MTI1IDUuODU3NDIgMy4wMDE5NSA2LjA1MjczIDMuMjM2MzNDNi4yNTE5NSAzLjQ2NjggNi40MDQzIDMuNzQwMjMgNi41MDk3NyA0LjA1NjY0QzYuNjE5MTQgNC4zNjkxNCA2LjY3MzgzIDQuNzIwNyA2LjY3MzgzIDUuMTExMzNINS4wNDQ5MkM1LjA0NDkyIDQuNjM4NjcgNC45Mzc1IDQuMjgxMjUgNC43MjI2NiA0LjAzOTA2QzQuNTA3ODEgMy43OTI5NyA0LjIxNjggMy42Njk5MiAzLjg0OTYxIDMuNjY5OTJDMy42NTAzOSAzLjY2OTkyIDMuNDc2NTYgMy42OTcyNyAzLjMyODEyIDMuNzUxOTVDMy4xODM1OSAzLjgwMjczIDMuMDY0NDUgMy44NzY5NSAyLjk3MDcgMy45NzQ2MUMyLjg3Njk1IDQuMDY4MzYgMi44MDY2NCA0LjE3OTY5IDIuNzU5NzcgNC4zMDg1OUMyLjcxNjggNC40Mzc1IDIuNjk1MzEgNC41NzgxMiAyLjY5NTMxIDQuNzMwNDdDMi42OTUzMSA0Ljg4MjgxIDIuNzE2OCA1LjAxOTUzIDIuNzU5NzcgNS4xNDA2MkMyLjgwNjY0IDUuMjU3ODEgMi44ODI4MSA1LjM2NzE5IDIuOTg4MjggNS40Njg3NUMzLjA5NzY2IDUuNTcwMzEgMy4yNDAyMyA1LjY2Nzk3IDMuNDE2MDIgNS43NjE3MkMzLjU5MTggNS44NTE1NiAzLjgxMDU1IDUuOTQzMzYgNC4wNzIyNyA2LjAzNzExQzQuNDY2OCA2LjE4NTU1IDQuODI0MjIgNi4zMzk4NCA1LjE0NDUzIDYuNUM1LjQ2NDg0IDYuNjU2MjUgNS43MzgyOCA2LjgzOTg0IDUuOTY0ODQgNy4wNTA3OEM2LjE5NTMxIDcuMjU3ODEgNi4zNzEwOSA3LjUgNi40OTIxOSA3Ljc3NzM0QzYuNjE3MTkgOC4wNTA3OCA2LjY3OTY5IDguMzc1IDYuNjc5NjkgOC43NUM2LjY3OTY5IDkuMDkzNzUgNi42MjMwNSA5LjQwNDMgNi41MDk3NyA5LjY4MTY0QzYuMzk2NDggOS45NTUwOCA2LjIzNDM4IDEwLjE5MTQgNi4wMjM0NCAxMC4zOTA2QzUuODEyNSAxMC41ODk4IDUuNTU4NTkgMTAuNzUgNS4yNjE3MiAxMC44NzExQzQuOTY0ODQgMTAuOTg4MyA0LjYzMjgxIDExLjA2NDUgNC4yNjU2MiAxMS4wOTk2VjEyLjI0OEgzLjMzMzk4VjExLjA5OTZDMy4wMDE5NSAxMS4wNjg0IDIuNjc5NjkgMTAuOTk2MSAyLjM2NzE5IDEwLjg4MjhDMi4wNTQ2OSAxMC43NjU2IDEuNzc3MzQgMTAuNTk3NyAxLjUzNTE2IDEwLjM3ODlDMS4yOTY4OCAxMC4xNjAyIDEuMTA1NDcgOS44ODQ3NyAwLjk2MDkzOCA5LjU1MjczQzAuODE2NDA2IDkuMjE2OCAwLjc0NDE0MSA4LjgxNDQ1IDAuNzQ0MTQxIDguMzQ1N0gyLjM3ODkxQzIuMzc4OTEgOC42MjY5NSAyLjQxOTkyIDguODYzMjggMi41MDE5NSA5LjA1NDY5QzIuNTgzOTggOS4yNDIxOSAyLjY4OTQ1IDkuMzkyNTggMi44MTgzNiA5LjUwNTg2QzIuOTUxMTcgOS42MTUyMyAzLjEwMTU2IDkuNjkzMzYgMy4yNjk1MyA5Ljc0MDIzQzMuNDM3NSA5Ljc4NzExIDMuNjA5MzggOS44MTA1NSAzLjc4NTE2IDkuODEwNTVDNC4yMDMxMiA5LjgxMDU1IDQuNTE5NTMgOS43MTI4OSA0LjczNDM4IDkuNTE3NThDNC45NDkyMiA5LjMyMjI3IDUuMDU2NjQgOS4wNzAzMSA1LjA1NjY0IDguNzYxNzJaTTEzLjQxOCAxMi4yNzE1SDguMDc0MjJWMTFIMTMuNDE4VjEyLjI3MTVaIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzLjk1MjY0IDYpIiBmaWxsPSJ3aGl0ZSIvPgo8L3N2Zz4K);
  --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTUgMTVIM3YyaDEydi0yem0wLThIM3YyaDEyVjd6TTMgMTNoMTh2LTJIM3Yyem0wIDhoMTh2LTJIM3Yyek0zIDN2MmgxOFYzSDN6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-toc: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik03LDVIMjFWN0g3VjVNNywxM1YxMUgyMVYxM0g3TTQsNC41QTEuNSwxLjUgMCAwLDEgNS41LDZBMS41LDEuNSAwIDAsMSA0LDcuNUExLjUsMS41IDAgMCwxIDIuNSw2QTEuNSwxLjUgMCAwLDEgNCw0LjVNNCwxMC41QTEuNSwxLjUgMCAwLDEgNS41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMy41QTEuNSwxLjUgMCAwLDEgMi41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMC41TTcsMTlWMTdIMjFWMTlIN000LDE2LjVBMS41LDEuNSAwIDAsMSA1LjUsMThBMS41LDEuNSAwIDAsMSA0LDE5LjVBMS41LDEuNSAwIDAsMSAyLjUsMThBMS41LDEuNSAwIDAsMSA0LDE2LjVaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tree-view: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMiAxMVYzaC03djNIOVYzSDJ2OGg3VjhoMnYxMGg0djNoN3YtOGgtN3YzaC0yVjhoMnYzeiIvPgogICAgPC9nPgo8L3N2Zz4=);
  --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
  --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
}

/* Icon CSS class declarations */

.jp-AddIcon {
  background-image: var(--jp-icon-add);
}
.jp-BugIcon {
  background-image: var(--jp-icon-bug);
}
.jp-BuildIcon {
  background-image: var(--jp-icon-build);
}
.jp-CaretDownEmptyIcon {
  background-image: var(--jp-icon-caret-down-empty);
}
.jp-CaretDownEmptyThinIcon {
  background-image: var(--jp-icon-caret-down-empty-thin);
}
.jp-CaretDownIcon {
  background-image: var(--jp-icon-caret-down);
}
.jp-CaretLeftIcon {
  background-image: var(--jp-icon-caret-left);
}
.jp-CaretRightIcon {
  background-image: var(--jp-icon-caret-right);
}
.jp-CaretUpEmptyThinIcon {
  background-image: var(--jp-icon-caret-up-empty-thin);
}
.jp-CaretUpIcon {
  background-image: var(--jp-icon-caret-up);
}
.jp-CaseSensitiveIcon {
  background-image: var(--jp-icon-case-sensitive);
}
.jp-CheckIcon {
  background-image: var(--jp-icon-check);
}
.jp-CircleEmptyIcon {
  background-image: var(--jp-icon-circle-empty);
}
.jp-CircleIcon {
  background-image: var(--jp-icon-circle);
}
.jp-ClearIcon {
  background-image: var(--jp-icon-clear);
}
.jp-CloseIcon {
  background-image: var(--jp-icon-close);
}
.jp-CodeIcon {
  background-image: var(--jp-icon-code);
}
.jp-ConsoleIcon {
  background-image: var(--jp-icon-console);
}
.jp-CopyIcon {
  background-image: var(--jp-icon-copy);
}
.jp-CopyrightIcon {
  background-image: var(--jp-icon-copyright);
}
.jp-CutIcon {
  background-image: var(--jp-icon-cut);
}
.jp-DownloadIcon {
  background-image: var(--jp-icon-download);
}
.jp-EditIcon {
  background-image: var(--jp-icon-edit);
}
.jp-EllipsesIcon {
  background-image: var(--jp-icon-ellipses);
}
.jp-ExtensionIcon {
  background-image: var(--jp-icon-extension);
}
.jp-FastForwardIcon {
  background-image: var(--jp-icon-fast-forward);
}
.jp-FileIcon {
  background-image: var(--jp-icon-file);
}
.jp-FileUploadIcon {
  background-image: var(--jp-icon-file-upload);
}
.jp-FilterListIcon {
  background-image: var(--jp-icon-filter-list);
}
.jp-FolderIcon {
  background-image: var(--jp-icon-folder);
}
.jp-Html5Icon {
  background-image: var(--jp-icon-html5);
}
.jp-ImageIcon {
  background-image: var(--jp-icon-image);
}
.jp-InspectorIcon {
  background-image: var(--jp-icon-inspector);
}
.jp-JsonIcon {
  background-image: var(--jp-icon-json);
}
.jp-JuliaIcon {
  background-image: var(--jp-icon-julia);
}
.jp-JupyterFaviconIcon {
  background-image: var(--jp-icon-jupyter-favicon);
}
.jp-JupyterIcon {
  background-image: var(--jp-icon-jupyter);
}
.jp-JupyterlabWordmarkIcon {
  background-image: var(--jp-icon-jupyterlab-wordmark);
}
.jp-KernelIcon {
  background-image: var(--jp-icon-kernel);
}
.jp-KeyboardIcon {
  background-image: var(--jp-icon-keyboard);
}
.jp-LauncherIcon {
  background-image: var(--jp-icon-launcher);
}
.jp-LineFormIcon {
  background-image: var(--jp-icon-line-form);
}
.jp-LinkIcon {
  background-image: var(--jp-icon-link);
}
.jp-ListIcon {
  background-image: var(--jp-icon-list);
}
.jp-ListingsInfoIcon {
  background-image: var(--jp-icon-listings-info);
}
.jp-MarkdownIcon {
  background-image: var(--jp-icon-markdown);
}
.jp-NewFolderIcon {
  background-image: var(--jp-icon-new-folder);
}
.jp-NotTrustedIcon {
  background-image: var(--jp-icon-not-trusted);
}
.jp-NotebookIcon {
  background-image: var(--jp-icon-notebook);
}
.jp-NumberingIcon {
  background-image: var(--jp-icon-numbering);
}
.jp-OfflineBoltIcon {
  background-image: var(--jp-icon-offline-bolt);
}
.jp-PaletteIcon {
  background-image: var(--jp-icon-palette);
}
.jp-PasteIcon {
  background-image: var(--jp-icon-paste);
}
.jp-PdfIcon {
  background-image: var(--jp-icon-pdf);
}
.jp-PythonIcon {
  background-image: var(--jp-icon-python);
}
.jp-RKernelIcon {
  background-image: var(--jp-icon-r-kernel);
}
.jp-ReactIcon {
  background-image: var(--jp-icon-react);
}
.jp-RedoIcon {
  background-image: var(--jp-icon-redo);
}
.jp-RefreshIcon {
  background-image: var(--jp-icon-refresh);
}
.jp-RegexIcon {
  background-image: var(--jp-icon-regex);
}
.jp-RunIcon {
  background-image: var(--jp-icon-run);
}
.jp-RunningIcon {
  background-image: var(--jp-icon-running);
}
.jp-SaveIcon {
  background-image: var(--jp-icon-save);
}
.jp-SearchIcon {
  background-image: var(--jp-icon-search);
}
.jp-SettingsIcon {
  background-image: var(--jp-icon-settings);
}
.jp-SpreadsheetIcon {
  background-image: var(--jp-icon-spreadsheet);
}
.jp-StopIcon {
  background-image: var(--jp-icon-stop);
}
.jp-TabIcon {
  background-image: var(--jp-icon-tab);
}
.jp-TableRowsIcon {
  background-image: var(--jp-icon-table-rows);
}
.jp-TagIcon {
  background-image: var(--jp-icon-tag);
}
.jp-TerminalIcon {
  background-image: var(--jp-icon-terminal);
}
.jp-TextEditorIcon {
  background-image: var(--jp-icon-text-editor);
}
.jp-TocIcon {
  background-image: var(--jp-icon-toc);
}
.jp-TreeViewIcon {
  background-image: var(--jp-icon-tree-view);
}
.jp-TrustedIcon {
  background-image: var(--jp-icon-trusted);
}
.jp-UndoIcon {
  background-image: var(--jp-icon-undo);
}
.jp-VegaIcon {
  background-image: var(--jp-icon-vega);
}
.jp-YamlIcon {
  background-image: var(--jp-icon-yaml);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

.jp-Icon,
.jp-MaterialIcon {
  background-position: center;
  background-repeat: no-repeat;
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-cover {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

/**
 * (DEPRECATED) Support for specific CSS icon sizes
 */

.jp-Icon-16 {
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-18 {
  background-size: 18px;
  min-width: 18px;
  min-height: 18px;
}

.jp-Icon-20 {
  background-size: 20px;
  min-width: 20px;
  min-height: 20px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for icons as inline SVG HTMLElements
 */

/* recolor the primary elements of an icon */
.jp-icon0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}
/* recolor the accent elements of an icon */
.jp-icon-accent0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-accent1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-accent2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-accent3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-accent4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-accent0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-accent1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-accent2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-accent3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-accent4[stroke] {
  stroke: var(--jp-layout-color4);
}
/* set the color of an icon to transparent */
.jp-icon-none[fill] {
  fill: none;
}

.jp-icon-none[stroke] {
  stroke: none;
}
/* brand icon colors. Same for light and dark */
.jp-icon-brand0[fill] {
  fill: var(--jp-brand-color0);
}
.jp-icon-brand1[fill] {
  fill: var(--jp-brand-color1);
}
.jp-icon-brand2[fill] {
  fill: var(--jp-brand-color2);
}
.jp-icon-brand3[fill] {
  fill: var(--jp-brand-color3);
}
.jp-icon-brand4[fill] {
  fill: var(--jp-brand-color4);
}

.jp-icon-brand0[stroke] {
  stroke: var(--jp-brand-color0);
}
.jp-icon-brand1[stroke] {
  stroke: var(--jp-brand-color1);
}
.jp-icon-brand2[stroke] {
  stroke: var(--jp-brand-color2);
}
.jp-icon-brand3[stroke] {
  stroke: var(--jp-brand-color3);
}
.jp-icon-brand4[stroke] {
  stroke: var(--jp-brand-color4);
}
/* warn icon colors. Same for light and dark */
.jp-icon-warn0[fill] {
  fill: var(--jp-warn-color0);
}
.jp-icon-warn1[fill] {
  fill: var(--jp-warn-color1);
}
.jp-icon-warn2[fill] {
  fill: var(--jp-warn-color2);
}
.jp-icon-warn3[fill] {
  fill: var(--jp-warn-color3);
}

.jp-icon-warn0[stroke] {
  stroke: var(--jp-warn-color0);
}
.jp-icon-warn1[stroke] {
  stroke: var(--jp-warn-color1);
}
.jp-icon-warn2[stroke] {
  stroke: var(--jp-warn-color2);
}
.jp-icon-warn3[stroke] {
  stroke: var(--jp-warn-color3);
}
/* icon colors that contrast well with each other and most backgrounds */
.jp-icon-contrast0[fill] {
  fill: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[fill] {
  fill: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[fill] {
  fill: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[fill] {
  fill: var(--jp-icon-contrast-color3);
}

.jp-icon-contrast0[stroke] {
  stroke: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[stroke] {
  stroke: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[stroke] {
  stroke: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[stroke] {
  stroke: var(--jp-icon-contrast-color3);
}

/* CSS for icons in selected items in the settings editor */
#setting-editor .jp-PluginList .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
#setting-editor
  .jp-PluginList
  .jp-mod-selected
  .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected filebrowser listing items */
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected tabs in the sidebar tab manager */
#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable[fill] {
  fill: #fff;
}

#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable[fill] {
  fill: var(--jp-brand-color1);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable-inverse[fill] {
  fill: #fff;
}

/**
 * TODO: come up with non css-hack solution for showing the busy icon on top
 *  of the close icon
 * CSS for complex behavior of close icon of tabs in the sidebar tab manager
 */
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-dirty.jp-mod-active
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: #fff;
}

/**
* TODO: come up with non css-hack solution for showing the busy icon on top
*  of the close icon
* CSS for complex behavior of close icon of tabs in the main area tabbar
*/
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

/* CSS for icons in status bar */
#jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

#jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
/* special handling for splash icon CSS. While the theme CSS reloads during
   splash, the splash icon can loose theming. To prevent that, we set a
   default for its color variable */
:root {
  --jp-warn-color0: var(--md-orange-700);
}

/* not sure what to do with this one, used in filebrowser listing */
.jp-DragIcon {
  margin-right: 4px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for alt colors for icons as inline SVG HTMLElements
 */

/* alt recolor the primary elements of an icon */
.jp-icon-alt .jp-icon0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-alt .jp-icon0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* alt recolor the accent elements of an icon */
.jp-icon-alt .jp-icon-accent0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-alt .jp-icon-accent0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-icon-hoverShow:not(:hover) svg {
  display: none !important;
}

/**
 * Support for hover colors for icons as inline SVG HTMLElements
 */

/**
 * regular colors
 */

/* recolor the primary elements of an icon */
.jp-icon-hover :hover .jp-icon0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-hover :hover .jp-icon-none-hover[fill] {
  fill: none;
}

.jp-icon-hover :hover .jp-icon-none-hover[stroke] {
  stroke: none;
}

/**
 * inverse colors
 */

/* inverse recolor the primary elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* inverse recolor the accent elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-switch {
  display: flex;
  align-items: center;
  padding-left: 4px;
  padding-right: 4px;
  font-size: var(--jp-ui-font-size1);
  background-color: transparent;
  color: var(--jp-ui-font-color1);
  border: none;
  height: 20px;
}

.jp-switch:hover {
  background-color: var(--jp-layout-color2);
}

.jp-switch-label {
  margin-right: 5px;
}

.jp-switch-track {
  cursor: pointer;
  background-color: var(--jp-border-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
  height: 16px;
  width: 35px;
  position: relative;
}

.jp-switch-track::before {
  content: '';
  position: absolute;
  height: 10px;
  width: 10px;
  margin: 3px;
  left: 0px;
  background-color: var(--jp-ui-inverse-font-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

.jp-switch[aria-checked='true'] .jp-switch-track {
  background-color: var(--jp-warn-color0);
}

.jp-switch[aria-checked='true'] .jp-switch-track::before {
  /* track width (35) - margins (3 + 3) - thumb width (10) */
  left: 19px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* Sibling imports */

/* Override Blueprint's _reset.scss styles */
html {
  box-sizing: unset;
}

*,
*::before,
*::after {
  box-sizing: unset;
}

body {
  color: unset;
  font-family: var(--jp-ui-font-family);
}

p {
  margin-top: unset;
  margin-bottom: unset;
}

small {
  font-size: unset;
}

strong {
  font-weight: unset;
}

/* Override Blueprint's _typography.scss styles */
a {
  text-decoration: unset;
  color: unset;
}
a:hover {
  text-decoration: unset;
  color: unset;
}

/* Override Blueprint's _accessibility.scss styles */
:focus {
  outline: unset;
  outline-offset: unset;
  -moz-outline-radius: unset;
}

/* Styles for ui-components */
.jp-Button {
  border-radius: var(--jp-border-radius);
  padding: 0px 12px;
  font-size: var(--jp-ui-font-size1);
}

/* Use our own theme for hover styles */
button.jp-Button.bp3-button.bp3-minimal:hover {
  background-color: var(--jp-layout-color2);
}
.jp-Button.minimal {
  color: unset !important;
}

.jp-Button.jp-ToolbarButtonComponent {
  text-transform: none;
}

.jp-InputGroup input {
  box-sizing: border-box;
  border-radius: 0;
  background-color: transparent;
  color: var(--jp-ui-font-color0);
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.jp-InputGroup input:focus {
  box-shadow: inset 0 0 0 var(--jp-border-width)
      var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-InputGroup input::placeholder,
input::placeholder {
  color: var(--jp-ui-font-color3);
}

.jp-BPIcon {
  display: inline-block;
  vertical-align: middle;
  margin: auto;
}

/* Stop blueprint futzing with our icon fills */
.bp3-icon.jp-BPIcon > svg:not([fill]) {
  fill: var(--jp-inverse-layout-color3);
}

.jp-InputGroupAction {
  padding: 6px;
}

.jp-HTMLSelect.jp-DefaultStyle select {
  background-color: initial;
  border: none;
  border-radius: 0;
  box-shadow: none;
  color: var(--jp-ui-font-color0);
  display: block;
  font-size: var(--jp-ui-font-size1);
  height: 24px;
  line-height: 14px;
  padding: 0 25px 0 10px;
  text-align: left;
  -moz-appearance: none;
  -webkit-appearance: none;
}

/* Use our own theme for hover and option styles */
.jp-HTMLSelect.jp-DefaultStyle select:hover,
.jp-HTMLSelect.jp-DefaultStyle select > option {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color0);
}
select {
  box-sizing: border-box;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapse {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-top: 1px solid var(--jp-border-color2);
  border-bottom: 1px solid var(--jp-border-color2);
}

.jp-Collapse-header {
  padding: 1px 12px;
  color: var(--jp-ui-font-color1);
  background-color: var(--jp-layout-color1);
  font-size: var(--jp-ui-font-size2);
}

.jp-Collapse-header:hover {
  background-color: var(--jp-layout-color2);
}

.jp-Collapse-contents {
  padding: 0px 12px 0px 12px;
  background-color: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-commandpalette-search-height: 28px;
}

/*-----------------------------------------------------------------------------
| Overall styles
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  padding-bottom: 0px;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Modal variant
|----------------------------------------------------------------------------*/

.jp-ModalCommandPalette {
  position: absolute;
  z-index: 10000;
  top: 38px;
  left: 30%;
  margin: 0;
  padding: 4px;
  width: 40%;
  box-shadow: var(--jp-elevation-z4);
  border-radius: 4px;
  background: var(--jp-layout-color0);
}

.jp-ModalCommandPalette .lm-CommandPalette {
  max-height: 40vh;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-close-icon::after {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-header {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-item {
  margin-left: 4px;
  margin-right: 4px;
}

.jp-ModalCommandPalette
  .lm-CommandPalette
  .lm-CommandPalette-item.lm-mod-disabled {
  display: none;
}

/*-----------------------------------------------------------------------------
| Search
|----------------------------------------------------------------------------*/

.lm-CommandPalette-search {
  padding: 4px;
  background-color: var(--jp-layout-color1);
  z-index: 2;
}

.lm-CommandPalette-wrapper {
  overflow: overlay;
  padding: 0px 9px;
  background-color: var(--jp-input-active-background);
  height: 30px;
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
  box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-SearchIconGroup {
  color: white;
  background-color: var(--jp-brand-color1);
  position: absolute;
  top: 4px;
  right: 4px;
  padding: 5px 5px 1px 5px;
}

.jp-SearchIconGroup svg {
  height: 20px;
  width: 20px;
}

.jp-SearchIconGroup .jp-icon3[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-input {
  background: transparent;
  width: calc(100% - 18px);
  float: left;
  border: none;
  outline: none;
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  line-height: var(--jp-private-commandpalette-search-height);
}

.lm-CommandPalette-input::-webkit-input-placeholder,
.lm-CommandPalette-input::-moz-placeholder,
.lm-CommandPalette-input:-ms-input-placeholder {
  color: var(--jp-ui-font-color2);
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Results
|----------------------------------------------------------------------------*/

.lm-CommandPalette-header:first-child {
  margin-top: 0px;
}

.lm-CommandPalette-header {
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin-top: 8px;
  padding: 8px 0 8px 12px;
  text-transform: uppercase;
}

.lm-CommandPalette-header.lm-mod-active {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-header > mark {
  background-color: transparent;
  font-weight: bold;
  color: var(--jp-ui-font-color1);
}

.lm-CommandPalette-item {
  padding: 4px 12px 4px 4px;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  font-weight: 400;
  display: flex;
}

.lm-CommandPalette-item.lm-mod-disabled {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item.lm-mod-active {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active .jp-icon-selectable[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-itemContent {
  overflow: hidden;
}

.lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.lm-CommandPalette-item.lm-mod-disabled mark {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item .lm-CommandPalette-itemIcon {
  margin: 0 4px 0 0;
  position: relative;
  width: 16px;
  top: 2px;
  flex: 0 0 auto;
}

.lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
  opacity: 0.6;
}

.lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemCaption {
  display: none;
}

.lm-CommandPalette-content {
  background-color: var(--jp-layout-color1);
}

.lm-CommandPalette-content:empty:after {
  content: 'No results';
  margin: auto;
  margin-top: 20px;
  width: 100px;
  display: block;
  font-size: var(--jp-ui-font-size2);
  font-family: var(--jp-ui-font-family);
  font-weight: lighter;
}

.lm-CommandPalette-emptyMessage {
  text-align: center;
  margin-top: 24px;
  line-height: 1.32;
  padding: 0px 8px;
  color: var(--jp-content-font-color3);
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Dialog {
  position: absolute;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  top: 0px;
  left: 0px;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-dialog-background);
}

.jp-Dialog-content {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  background: var(--jp-layout-color1);
  padding: 24px;
  padding-bottom: 12px;
  min-width: 300px;
  min-height: 150px;
  max-width: 1000px;
  max-height: 500px;
  box-sizing: border-box;
  box-shadow: var(--jp-elevation-z20);
  word-wrap: break-word;
  border-radius: var(--jp-border-radius);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color1);
  resize: both;
}

.jp-Dialog-button {
  overflow: visible;
}

button.jp-Dialog-button:focus {
  outline: 1px solid var(--jp-brand-color1);
  outline-offset: 4px;
  -moz-outline-radius: 0px;
}

button.jp-Dialog-button:focus::-moz-focus-inner {
  border: 0;
}

button.jp-Dialog-close-button {
  padding: 0;
  height: 100%;
  min-width: unset;
  min-height: unset;
}

.jp-Dialog-header {
  display: flex;
  justify-content: space-between;
  flex: 0 0 auto;
  padding-bottom: 12px;
  font-size: var(--jp-ui-font-size3);
  font-weight: 400;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-body {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  font-size: var(--jp-ui-font-size1);
  background: var(--jp-layout-color1);
  overflow: auto;
}

.jp-Dialog-footer {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  flex: 0 0 auto;
  margin-left: -12px;
  margin-right: -12px;
  padding: 12px;
}

.jp-Dialog-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.jp-Dialog-body > .jp-select-wrapper {
  width: 100%;
}

.jp-Dialog-body > button {
  padding: 0px 16px;
}

.jp-Dialog-body > label {
  line-height: 1.4;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-button.jp-mod-styled:not(:last-child) {
  margin-right: 12px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-HoverBox {
  position: fixed;
}

.jp-HoverBox.jp-mod-outofview {
  display: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-IFrame {
  width: 100%;
  height: 100%;
}

.jp-IFrame > iframe {
  border: none;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-IFrame {
  position: relative;
}

body.lm-mod-override-cursor .jp-IFrame:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

.jp-Input-Boolean-Dialog {
  flex-direction: row-reverse;
  align-items: end;
  width: 100%;
}

.jp-Input-Boolean-Dialog > label {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MainAreaWidget > :focus {
  outline: none;
}

/**
 * google-material-color v1.2.6
 * https://github.com/danlevan/google-material-color
 */
:root {
  --md-red-50: #ffebee;
  --md-red-100: #ffcdd2;
  --md-red-200: #ef9a9a;
  --md-red-300: #e57373;
  --md-red-400: #ef5350;
  --md-red-500: #f44336;
  --md-red-600: #e53935;
  --md-red-700: #d32f2f;
  --md-red-800: #c62828;
  --md-red-900: #b71c1c;
  --md-red-A100: #ff8a80;
  --md-red-A200: #ff5252;
  --md-red-A400: #ff1744;
  --md-red-A700: #d50000;

  --md-pink-50: #fce4ec;
  --md-pink-100: #f8bbd0;
  --md-pink-200: #f48fb1;
  --md-pink-300: #f06292;
  --md-pink-400: #ec407a;
  --md-pink-500: #e91e63;
  --md-pink-600: #d81b60;
  --md-pink-700: #c2185b;
  --md-pink-800: #ad1457;
  --md-pink-900: #880e4f;
  --md-pink-A100: #ff80ab;
  --md-pink-A200: #ff4081;
  --md-pink-A400: #f50057;
  --md-pink-A700: #c51162;

  --md-purple-50: #f3e5f5;
  --md-purple-100: #e1bee7;
  --md-purple-200: #ce93d8;
  --md-purple-300: #ba68c8;
  --md-purple-400: #ab47bc;
  --md-purple-500: #9c27b0;
  --md-purple-600: #8e24aa;
  --md-purple-700: #7b1fa2;
  --md-purple-800: #6a1b9a;
  --md-purple-900: #4a148c;
  --md-purple-A100: #ea80fc;
  --md-purple-A200: #e040fb;
  --md-purple-A400: #d500f9;
  --md-purple-A700: #aa00ff;

  --md-deep-purple-50: #ede7f6;
  --md-deep-purple-100: #d1c4e9;
  --md-deep-purple-200: #b39ddb;
  --md-deep-purple-300: #9575cd;
  --md-deep-purple-400: #7e57c2;
  --md-deep-purple-500: #673ab7;
  --md-deep-purple-600: #5e35b1;
  --md-deep-purple-700: #512da8;
  --md-deep-purple-800: #4527a0;
  --md-deep-purple-900: #311b92;
  --md-deep-purple-A100: #b388ff;
  --md-deep-purple-A200: #7c4dff;
  --md-deep-purple-A400: #651fff;
  --md-deep-purple-A700: #6200ea;

  --md-indigo-50: #e8eaf6;
  --md-indigo-100: #c5cae9;
  --md-indigo-200: #9fa8da;
  --md-indigo-300: #7986cb;
  --md-indigo-400: #5c6bc0;
  --md-indigo-500: #3f51b5;
  --md-indigo-600: #3949ab;
  --md-indigo-700: #303f9f;
  --md-indigo-800: #283593;
  --md-indigo-900: #1a237e;
  --md-indigo-A100: #8c9eff;
  --md-indigo-A200: #536dfe;
  --md-indigo-A400: #3d5afe;
  --md-indigo-A700: #304ffe;

  --md-blue-50: #e3f2fd;
  --md-blue-100: #bbdefb;
  --md-blue-200: #90caf9;
  --md-blue-300: #64b5f6;
  --md-blue-400: #42a5f5;
  --md-blue-500: #2196f3;
  --md-blue-600: #1e88e5;
  --md-blue-700: #1976d2;
  --md-blue-800: #1565c0;
  --md-blue-900: #0d47a1;
  --md-blue-A100: #82b1ff;
  --md-blue-A200: #448aff;
  --md-blue-A400: #2979ff;
  --md-blue-A700: #2962ff;

  --md-light-blue-50: #e1f5fe;
  --md-light-blue-100: #b3e5fc;
  --md-light-blue-200: #81d4fa;
  --md-light-blue-300: #4fc3f7;
  --md-light-blue-400: #29b6f6;
  --md-light-blue-500: #03a9f4;
  --md-light-blue-600: #039be5;
  --md-light-blue-700: #0288d1;
  --md-light-blue-800: #0277bd;
  --md-light-blue-900: #01579b;
  --md-light-blue-A100: #80d8ff;
  --md-light-blue-A200: #40c4ff;
  --md-light-blue-A400: #00b0ff;
  --md-light-blue-A700: #0091ea;

  --md-cyan-50: #e0f7fa;
  --md-cyan-100: #b2ebf2;
  --md-cyan-200: #80deea;
  --md-cyan-300: #4dd0e1;
  --md-cyan-400: #26c6da;
  --md-cyan-500: #00bcd4;
  --md-cyan-600: #00acc1;
  --md-cyan-700: #0097a7;
  --md-cyan-800: #00838f;
  --md-cyan-900: #006064;
  --md-cyan-A100: #84ffff;
  --md-cyan-A200: #18ffff;
  --md-cyan-A400: #00e5ff;
  --md-cyan-A700: #00b8d4;

  --md-teal-50: #e0f2f1;
  --md-teal-100: #b2dfdb;
  --md-teal-200: #80cbc4;
  --md-teal-300: #4db6ac;
  --md-teal-400: #26a69a;
  --md-teal-500: #009688;
  --md-teal-600: #00897b;
  --md-teal-700: #00796b;
  --md-teal-800: #00695c;
  --md-teal-900: #004d40;
  --md-teal-A100: #a7ffeb;
  --md-teal-A200: #64ffda;
  --md-teal-A400: #1de9b6;
  --md-teal-A700: #00bfa5;

  --md-green-50: #e8f5e9;
  --md-green-100: #c8e6c9;
  --md-green-200: #a5d6a7;
  --md-green-300: #81c784;
  --md-green-400: #66bb6a;
  --md-green-500: #4caf50;
  --md-green-600: #43a047;
  --md-green-700: #388e3c;
  --md-green-800: #2e7d32;
  --md-green-900: #1b5e20;
  --md-green-A100: #b9f6ca;
  --md-green-A200: #69f0ae;
  --md-green-A400: #00e676;
  --md-green-A700: #00c853;

  --md-light-green-50: #f1f8e9;
  --md-light-green-100: #dcedc8;
  --md-light-green-200: #c5e1a5;
  --md-light-green-300: #aed581;
  --md-light-green-400: #9ccc65;
  --md-light-green-500: #8bc34a;
  --md-light-green-600: #7cb342;
  --md-light-green-700: #689f38;
  --md-light-green-800: #558b2f;
  --md-light-green-900: #33691e;
  --md-light-green-A100: #ccff90;
  --md-light-green-A200: #b2ff59;
  --md-light-green-A400: #76ff03;
  --md-light-green-A700: #64dd17;

  --md-lime-50: #f9fbe7;
  --md-lime-100: #f0f4c3;
  --md-lime-200: #e6ee9c;
  --md-lime-300: #dce775;
  --md-lime-400: #d4e157;
  --md-lime-500: #cddc39;
  --md-lime-600: #c0ca33;
  --md-lime-700: #afb42b;
  --md-lime-800: #9e9d24;
  --md-lime-900: #827717;
  --md-lime-A100: #f4ff81;
  --md-lime-A200: #eeff41;
  --md-lime-A400: #c6ff00;
  --md-lime-A700: #aeea00;

  --md-yellow-50: #fffde7;
  --md-yellow-100: #fff9c4;
  --md-yellow-200: #fff59d;
  --md-yellow-300: #fff176;
  --md-yellow-400: #ffee58;
  --md-yellow-500: #ffeb3b;
  --md-yellow-600: #fdd835;
  --md-yellow-700: #fbc02d;
  --md-yellow-800: #f9a825;
  --md-yellow-900: #f57f17;
  --md-yellow-A100: #ffff8d;
  --md-yellow-A200: #ffff00;
  --md-yellow-A400: #ffea00;
  --md-yellow-A700: #ffd600;

  --md-amber-50: #fff8e1;
  --md-amber-100: #ffecb3;
  --md-amber-200: #ffe082;
  --md-amber-300: #ffd54f;
  --md-amber-400: #ffca28;
  --md-amber-500: #ffc107;
  --md-amber-600: #ffb300;
  --md-amber-700: #ffa000;
  --md-amber-800: #ff8f00;
  --md-amber-900: #ff6f00;
  --md-amber-A100: #ffe57f;
  --md-amber-A200: #ffd740;
  --md-amber-A400: #ffc400;
  --md-amber-A700: #ffab00;

  --md-orange-50: #fff3e0;
  --md-orange-100: #ffe0b2;
  --md-orange-200: #ffcc80;
  --md-orange-300: #ffb74d;
  --md-orange-400: #ffa726;
  --md-orange-500: #ff9800;
  --md-orange-600: #fb8c00;
  --md-orange-700: #f57c00;
  --md-orange-800: #ef6c00;
  --md-orange-900: #e65100;
  --md-orange-A100: #ffd180;
  --md-orange-A200: #ffab40;
  --md-orange-A400: #ff9100;
  --md-orange-A700: #ff6d00;

  --md-deep-orange-50: #fbe9e7;
  --md-deep-orange-100: #ffccbc;
  --md-deep-orange-200: #ffab91;
  --md-deep-orange-300: #ff8a65;
  --md-deep-orange-400: #ff7043;
  --md-deep-orange-500: #ff5722;
  --md-deep-orange-600: #f4511e;
  --md-deep-orange-700: #e64a19;
  --md-deep-orange-800: #d84315;
  --md-deep-orange-900: #bf360c;
  --md-deep-orange-A100: #ff9e80;
  --md-deep-orange-A200: #ff6e40;
  --md-deep-orange-A400: #ff3d00;
  --md-deep-orange-A700: #dd2c00;

  --md-brown-50: #efebe9;
  --md-brown-100: #d7ccc8;
  --md-brown-200: #bcaaa4;
  --md-brown-300: #a1887f;
  --md-brown-400: #8d6e63;
  --md-brown-500: #795548;
  --md-brown-600: #6d4c41;
  --md-brown-700: #5d4037;
  --md-brown-800: #4e342e;
  --md-brown-900: #3e2723;

  --md-grey-50: #fafafa;
  --md-grey-100: #f5f5f5;
  --md-grey-200: #eeeeee;
  --md-grey-300: #e0e0e0;
  --md-grey-400: #bdbdbd;
  --md-grey-500: #9e9e9e;
  --md-grey-600: #757575;
  --md-grey-700: #616161;
  --md-grey-800: #424242;
  --md-grey-900: #212121;

  --md-blue-grey-50: #eceff1;
  --md-blue-grey-100: #cfd8dc;
  --md-blue-grey-200: #b0bec5;
  --md-blue-grey-300: #90a4ae;
  --md-blue-grey-400: #78909c;
  --md-blue-grey-500: #607d8b;
  --md-blue-grey-600: #546e7a;
  --md-blue-grey-700: #455a64;
  --md-blue-grey-800: #37474f;
  --md-blue-grey-900: #263238;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Spinner {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-layout-color0);
  outline: none;
}

.jp-SpinnerContent {
  font-size: 10px;
  margin: 50px auto;
  text-indent: -9999em;
  width: 3em;
  height: 3em;
  border-radius: 50%;
  background: var(--jp-brand-color3);
  background: linear-gradient(
    to right,
    #f37626 10%,
    rgba(255, 255, 255, 0) 42%
  );
  position: relative;
  animation: load3 1s infinite linear, fadeIn 1s;
}

.jp-SpinnerContent:before {
  width: 50%;
  height: 50%;
  background: #f37626;
  border-radius: 100% 0 0 0;
  position: absolute;
  top: 0;
  left: 0;
  content: '';
}

.jp-SpinnerContent:after {
  background: var(--jp-layout-color0);
  width: 75%;
  height: 75%;
  border-radius: 50%;
  content: '';
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes load3 {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

button.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: none;
  box-sizing: border-box;
  text-align: center;
  line-height: 32px;
  height: 32px;
  padding: 0px 12px;
  letter-spacing: 0.8px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input.jp-mod-styled {
  background: var(--jp-input-background);
  height: 28px;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color1);
  padding-left: 7px;
  padding-right: 7px;
  font-size: var(--jp-ui-font-size2);
  color: var(--jp-ui-font-color0);
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input[type='checkbox'].jp-mod-styled {
  appearance: checkbox;
  -webkit-appearance: checkbox;
  -moz-appearance: checkbox;
  height: auto;
}

input.jp-mod-styled:focus {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-FileDialog-Checkbox {
  margin-top: 35px;
  display: flex;
  flex-direction: row;
  align-items: end;
  width: 100%;
}

.jp-FileDialog-Checkbox > label {
  flex: 1 1 auto;
}

.jp-select-wrapper {
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 1px;
  background-color: var(--jp-layout-color1);
  height: 28px;
  box-sizing: border-box;
  margin-bottom: 12px;
}

.jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-input-active-background);
}

select.jp-mod-styled:hover {
  background-color: var(--jp-layout-color1);
  cursor: pointer;
  color: var(--jp-ui-font-color0);
  background-color: var(--jp-input-hover-background);
  box-shadow: inset 0 0px 1px rgba(0, 0, 0, 0.5);
}

select.jp-mod-styled {
  flex: 1 1 auto;
  height: 32px;
  width: 100%;
  font-size: var(--jp-ui-font-size2);
  background: var(--jp-input-background);
  color: var(--jp-ui-font-color0);
  padding: 0 25px 0 8px;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toolbar-height: calc(
    28px + var(--jp-border-width)
  ); /* leave 28px for content */
}

.jp-Toolbar {
  color: var(--jp-ui-font-color1);
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: 2px;
  z-index: 1;
  overflow-x: auto;
}

/* Toolbar items */

.jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
  flex-grow: 1;
  flex-shrink: 1;
}

.jp-Toolbar-item.jp-Toolbar-kernelStatus {
  display: inline-block;
  width: 32px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 16px;
}

.jp-Toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  display: flex;
  padding-left: 1px;
  padding-right: 1px;
  font-size: var(--jp-ui-font-size1);
  line-height: var(--jp-private-toolbar-height);
  height: 100%;
}

/* Toolbar buttons */

/* This is the div we use to wrap the react component into a Widget */
div.jp-ToolbarButton {
  color: transparent;
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px;
  margin: 0px;
}

button.jp-ToolbarButtonComponent {
  background: var(--jp-layout-color1);
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px 6px;
  margin: 0px;
  height: 24px;
  border-radius: var(--jp-border-radius);
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 14px;
  min-width: unset;
  min-height: unset;
}

button.jp-ToolbarButtonComponent:disabled {
  opacity: 0.4;
}

button.jp-ToolbarButtonComponent span {
  padding: 0px;
  flex: 0 0 auto;
}

button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
  font-size: var(--jp-ui-font-size1);
  line-height: 100%;
  padding-left: 2px;
  color: var(--jp-ui-font-color1);
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar.jp-Toolbar-micro {
  padding: 0;
  min-height: 0;
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar {
  border: none;
  box-shadow: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ body.p-mod-override-cursor *, /* </DEPRECATED> */
body.lm-mod-override-cursor * {
  cursor: inherit !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-JSONEditor {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.jp-JSONEditor-host {
  flex: 1 1 auto;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  background: var(--jp-layout-color0);
  min-height: 50px;
  padding: 1px;
}

.jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
  border-color: red;
  outline-color: red;
}

.jp-JSONEditor-header {
  display: flex;
  flex: 1 0 auto;
  padding: 0 0 0 12px;
}

.jp-JSONEditor-header label {
  flex: 0 0 auto;
}

.jp-JSONEditor-commitButton {
  height: 16px;
  width: 16px;
  background-size: 18px;
  background-repeat: no-repeat;
  background-position: center;
}

.jp-JSONEditor-host.jp-mod-focused {
  background-color: var(--jp-input-active-background);
  border: 1px solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

.jp-Editor.jp-mod-dropTarget {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

/* BASICS */

.CodeMirror {
  /* Set height, width, borders, and global font properties here */
  font-family: monospace;
  height: 300px;
  color: black;
  direction: ltr;
}

/* PADDING */

.CodeMirror-lines {
  padding: 4px 0; /* Vertical padding around content */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  padding: 0 4px; /* Horizontal padding of content */
}

.CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  background-color: white; /* The little square between H and V scrollbars */
}

/* GUTTER */

.CodeMirror-gutters {
  border-right: 1px solid #ddd;
  background-color: #f7f7f7;
  white-space: nowrap;
}
.CodeMirror-linenumbers {}
.CodeMirror-linenumber {
  padding: 0 3px 0 5px;
  min-width: 20px;
  text-align: right;
  color: #999;
  white-space: nowrap;
}

.CodeMirror-guttermarker { color: black; }
.CodeMirror-guttermarker-subtle { color: #999; }

/* CURSOR */

.CodeMirror-cursor {
  border-left: 1px solid black;
  border-right: none;
  width: 0;
}
/* Shown when moving in bi-directional text */
.CodeMirror div.CodeMirror-secondarycursor {
  border-left: 1px solid silver;
}
.cm-fat-cursor .CodeMirror-cursor {
  width: auto;
  border: 0 !important;
  background: #7e7;
}
.cm-fat-cursor div.CodeMirror-cursors {
  z-index: 1;
}
.cm-fat-cursor-mark {
  background-color: rgba(20, 255, 20, 0.5);
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
}
.cm-animate-fat-cursor {
  width: auto;
  border: 0;
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
  background-color: #7e7;
}
@-moz-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@-webkit-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}

/* Can style cursor different in overwrite (non-insert) mode */
.CodeMirror-overwrite .CodeMirror-cursor {}

.cm-tab { display: inline-block; text-decoration: inherit; }

.CodeMirror-rulers {
  position: absolute;
  left: 0; right: 0; top: -50px; bottom: 0;
  overflow: hidden;
}
.CodeMirror-ruler {
  border-left: 1px solid #ccc;
  top: 0; bottom: 0;
  position: absolute;
}

/* DEFAULT THEME */

.cm-s-default .cm-header {color: blue;}
.cm-s-default .cm-quote {color: #090;}
.cm-negative {color: #d44;}
.cm-positive {color: #292;}
.cm-header, .cm-strong {font-weight: bold;}
.cm-em {font-style: italic;}
.cm-link {text-decoration: underline;}
.cm-strikethrough {text-decoration: line-through;}

.cm-s-default .cm-keyword {color: #708;}
.cm-s-default .cm-atom {color: #219;}
.cm-s-default .cm-number {color: #164;}
.cm-s-default .cm-def {color: #00f;}
.cm-s-default .cm-variable,
.cm-s-default .cm-punctuation,
.cm-s-default .cm-property,
.cm-s-default .cm-operator {}
.cm-s-default .cm-variable-2 {color: #05a;}
.cm-s-default .cm-variable-3, .cm-s-default .cm-type {color: #085;}
.cm-s-default .cm-comment {color: #a50;}
.cm-s-default .cm-string {color: #a11;}
.cm-s-default .cm-string-2 {color: #f50;}
.cm-s-default .cm-meta {color: #555;}
.cm-s-default .cm-qualifier {color: #555;}
.cm-s-default .cm-builtin {color: #30a;}
.cm-s-default .cm-bracket {color: #997;}
.cm-s-default .cm-tag {color: #170;}
.cm-s-default .cm-attribute {color: #00c;}
.cm-s-default .cm-hr {color: #999;}
.cm-s-default .cm-link {color: #00c;}

.cm-s-default .cm-error {color: #f00;}
.cm-invalidchar {color: #f00;}

.CodeMirror-composing { border-bottom: 2px solid; }

/* Default styles for common addons */

div.CodeMirror span.CodeMirror-matchingbracket {color: #0b0;}
div.CodeMirror span.CodeMirror-nonmatchingbracket {color: #a22;}
.CodeMirror-matchingtag { background: rgba(255, 150, 0, .3); }
.CodeMirror-activeline-background {background: #e8f2ff;}

/* STOP */

/* The rest of this file contains styles related to the mechanics of
   the editor. You probably shouldn't touch them. */

.CodeMirror {
  position: relative;
  overflow: hidden;
  background: white;
}

.CodeMirror-scroll {
  overflow: scroll !important; /* Things will break if this is overridden */
  /* 50px is the magic margin used to hide the element's real scrollbars */
  /* See overflow: hidden in .CodeMirror */
  margin-bottom: -50px; margin-right: -50px;
  padding-bottom: 50px;
  height: 100%;
  outline: none; /* Prevent dragging from highlighting the element */
  position: relative;
}
.CodeMirror-sizer {
  position: relative;
  border-right: 50px solid transparent;
}

/* The fake, visible scrollbars. Used to force redraw during scrolling
   before actual scrolling happens, thus preventing shaking and
   flickering artifacts. */
.CodeMirror-vscrollbar, .CodeMirror-hscrollbar, .CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  position: absolute;
  z-index: 6;
  display: none;
  outline: none;
}
.CodeMirror-vscrollbar {
  right: 0; top: 0;
  overflow-x: hidden;
  overflow-y: scroll;
}
.CodeMirror-hscrollbar {
  bottom: 0; left: 0;
  overflow-y: hidden;
  overflow-x: scroll;
}
.CodeMirror-scrollbar-filler {
  right: 0; bottom: 0;
}
.CodeMirror-gutter-filler {
  left: 0; bottom: 0;
}

.CodeMirror-gutters {
  position: absolute; left: 0; top: 0;
  min-height: 100%;
  z-index: 3;
}
.CodeMirror-gutter {
  white-space: normal;
  height: 100%;
  display: inline-block;
  vertical-align: top;
  margin-bottom: -50px;
}
.CodeMirror-gutter-wrapper {
  position: absolute;
  z-index: 4;
  background: none !important;
  border: none !important;
}
.CodeMirror-gutter-background {
  position: absolute;
  top: 0; bottom: 0;
  z-index: 4;
}
.CodeMirror-gutter-elt {
  position: absolute;
  cursor: default;
  z-index: 4;
}
.CodeMirror-gutter-wrapper ::selection { background-color: transparent }
.CodeMirror-gutter-wrapper ::-moz-selection { background-color: transparent }

.CodeMirror-lines {
  cursor: text;
  min-height: 1px; /* prevents collapsing before first draw */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  /* Reset some styles that the rest of the page might have set */
  -moz-border-radius: 0; -webkit-border-radius: 0; border-radius: 0;
  border-width: 0;
  background: transparent;
  font-family: inherit;
  font-size: inherit;
  margin: 0;
  white-space: pre;
  word-wrap: normal;
  line-height: inherit;
  color: inherit;
  z-index: 2;
  position: relative;
  overflow: visible;
  -webkit-tap-highlight-color: transparent;
  -webkit-font-variant-ligatures: contextual;
  font-variant-ligatures: contextual;
}
.CodeMirror-wrap pre.CodeMirror-line,
.CodeMirror-wrap pre.CodeMirror-line-like {
  word-wrap: break-word;
  white-space: pre-wrap;
  word-break: normal;
}

.CodeMirror-linebackground {
  position: absolute;
  left: 0; right: 0; top: 0; bottom: 0;
  z-index: 0;
}

.CodeMirror-linewidget {
  position: relative;
  z-index: 2;
  padding: 0.1px; /* Force widget margins to stay inside of the container */
}

.CodeMirror-widget {}

.CodeMirror-rtl pre { direction: rtl; }

.CodeMirror-code {
  outline: none;
}

/* Force content-box sizing for the elements where we expect it */
.CodeMirror-scroll,
.CodeMirror-sizer,
.CodeMirror-gutter,
.CodeMirror-gutters,
.CodeMirror-linenumber {
  -moz-box-sizing: content-box;
  box-sizing: content-box;
}

.CodeMirror-measure {
  position: absolute;
  width: 100%;
  height: 0;
  overflow: hidden;
  visibility: hidden;
}

.CodeMirror-cursor {
  position: absolute;
  pointer-events: none;
}
.CodeMirror-measure pre { position: static; }

div.CodeMirror-cursors {
  visibility: hidden;
  position: relative;
  z-index: 3;
}
div.CodeMirror-dragcursors {
  visibility: visible;
}

.CodeMirror-focused div.CodeMirror-cursors {
  visibility: visible;
}

.CodeMirror-selected { background: #d9d9d9; }
.CodeMirror-focused .CodeMirror-selected { background: #d7d4f0; }
.CodeMirror-crosshair { cursor: crosshair; }
.CodeMirror-line::selection, .CodeMirror-line > span::selection, .CodeMirror-line > span > span::selection { background: #d7d4f0; }
.CodeMirror-line::-moz-selection, .CodeMirror-line > span::-moz-selection, .CodeMirror-line > span > span::-moz-selection { background: #d7d4f0; }

.cm-searching {
  background-color: #ffa;
  background-color: rgba(255, 255, 0, .4);
}

/* Used to force a border model for a node */
.cm-force-border { padding-right: .1px; }

@media print {
  /* Hide the cursor when printing */
  .CodeMirror div.CodeMirror-cursors {
    visibility: hidden;
  }
}

/* See issue #2901 */
.cm-tab-wrap-hack:after { content: ''; }

/* Help users use markselection to safely style text background */
span.CodeMirror-selectedtext { background: none; }

.CodeMirror-dialog {
  position: absolute;
  left: 0; right: 0;
  background: inherit;
  z-index: 15;
  padding: .1em .8em;
  overflow: hidden;
  color: inherit;
}

.CodeMirror-dialog-top {
  border-bottom: 1px solid #eee;
  top: 0;
}

.CodeMirror-dialog-bottom {
  border-top: 1px solid #eee;
  bottom: 0;
}

.CodeMirror-dialog input {
  border: none;
  outline: none;
  background: transparent;
  width: 20em;
  color: inherit;
  font-family: monospace;
}

.CodeMirror-dialog button {
  font-size: 70%;
}

.CodeMirror-foldmarker {
  color: blue;
  text-shadow: #b9f 1px 1px 2px, #b9f -1px -1px 2px, #b9f 1px -1px 2px, #b9f -1px 1px 2px;
  font-family: arial;
  line-height: .3;
  cursor: pointer;
}
.CodeMirror-foldgutter {
  width: .7em;
}
.CodeMirror-foldgutter-open,
.CodeMirror-foldgutter-folded {
  cursor: pointer;
}
.CodeMirror-foldgutter-open:after {
  content: "\25BE";
}
.CodeMirror-foldgutter-folded:after {
  content: "\25B8";
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.CodeMirror {
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  border: 0;
  border-radius: 0;
  height: auto;
  /* Changed to auto to autogrow */
}

.CodeMirror pre {
  padding: 0 var(--jp-code-padding);
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-dialog {
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* This causes https://github.com/jupyter/jupyterlab/issues/522 */
/* May not cause it not because we changed it! */
.CodeMirror-lines {
  padding: var(--jp-code-padding) 0;
}

.CodeMirror-linenumber {
  padding: 0 8px;
}

.jp-CodeMirrorEditor {
  cursor: text;
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}

/* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width1) solid
      var(--jp-editor-cursor-color);
  }
}

/* When zoomed out less than 33% */
@media screen and (min-width: 4320px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width2) solid
      var(--jp-editor-cursor-color);
  }
}

.CodeMirror.jp-mod-readOnly .CodeMirror-cursor {
  display: none;
}

.CodeMirror-gutters {
  border-right: 1px solid var(--jp-border-color2);
  background-color: var(--jp-layout-color0);
}

.jp-CollaboratorCursor {
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: none;
  border-bottom: 3px solid;
  background-clip: content-box;
  margin-left: -5px;
  margin-right: -5px;
}

.CodeMirror-selectedtext.cm-searching {
  background-color: var(--jp-search-selected-match-background-color) !important;
  color: var(--jp-search-selected-match-color) !important;
}

.cm-searching {
  background-color: var(
    --jp-search-unselected-match-background-color
  ) !important;
  color: var(--jp-search-unselected-match-color) !important;
}

.CodeMirror-focused .CodeMirror-selected {
  background-color: var(--jp-editor-selected-focused-background);
}

.CodeMirror-selected {
  background-color: var(--jp-editor-selected-background);
}

.jp-CollaboratorCursor-hover {
  position: absolute;
  z-index: 1;
  transform: translateX(-50%);
  color: white;
  border-radius: 3px;
  padding-left: 4px;
  padding-right: 4px;
  padding-top: 1px;
  padding-bottom: 1px;
  text-align: center;
  font-size: var(--jp-ui-font-size1);
  white-space: nowrap;
}

.jp-CodeMirror-ruler {
  border-left: 1px dashed var(--jp-border-color2);
}

/**
 * Here is our jupyter theme for CodeMirror syntax highlighting
 * This is used in our marked.js syntax highlighting and CodeMirror itself
 * The string "jupyter" is set in ../codemirror/widget.DEFAULT_CODEMIRROR_THEME
 * This came from the classic notebook, which came form highlight.js/GitHub
 */

/**
 * CodeMirror themes are handling the background/color in this way. This works
 * fine for CodeMirror editors outside the notebook, but the notebook styles
 * these things differently.
 */
.CodeMirror.cm-s-jupyter {
  background: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* In the notebook, we want this styling to be handled by its container */
.jp-CodeConsole .CodeMirror.cm-s-jupyter,
.jp-Notebook .CodeMirror.cm-s-jupyter {
  background: transparent;
}

.cm-s-jupyter .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}
.cm-s-jupyter span.cm-keyword {
  color: var(--jp-mirror-editor-keyword-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-atom {
  color: var(--jp-mirror-editor-atom-color);
}
.cm-s-jupyter span.cm-number {
  color: var(--jp-mirror-editor-number-color);
}
.cm-s-jupyter span.cm-def {
  color: var(--jp-mirror-editor-def-color);
}
.cm-s-jupyter span.cm-variable {
  color: var(--jp-mirror-editor-variable-color);
}
.cm-s-jupyter span.cm-variable-2 {
  color: var(--jp-mirror-editor-variable-2-color);
}
.cm-s-jupyter span.cm-variable-3 {
  color: var(--jp-mirror-editor-variable-3-color);
}
.cm-s-jupyter span.cm-punctuation {
  color: var(--jp-mirror-editor-punctuation-color);
}
.cm-s-jupyter span.cm-property {
  color: var(--jp-mirror-editor-property-color);
}
.cm-s-jupyter span.cm-operator {
  color: var(--jp-mirror-editor-operator-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-comment {
  color: var(--jp-mirror-editor-comment-color);
  font-style: italic;
}
.cm-s-jupyter span.cm-string {
  color: var(--jp-mirror-editor-string-color);
}
.cm-s-jupyter span.cm-string-2 {
  color: var(--jp-mirror-editor-string-2-color);
}
.cm-s-jupyter span.cm-meta {
  color: var(--jp-mirror-editor-meta-color);
}
.cm-s-jupyter span.cm-qualifier {
  color: var(--jp-mirror-editor-qualifier-color);
}
.cm-s-jupyter span.cm-builtin {
  color: var(--jp-mirror-editor-builtin-color);
}
.cm-s-jupyter span.cm-bracket {
  color: var(--jp-mirror-editor-bracket-color);
}
.cm-s-jupyter span.cm-tag {
  color: var(--jp-mirror-editor-tag-color);
}
.cm-s-jupyter span.cm-attribute {
  color: var(--jp-mirror-editor-attribute-color);
}
.cm-s-jupyter span.cm-header {
  color: var(--jp-mirror-editor-header-color);
}
.cm-s-jupyter span.cm-quote {
  color: var(--jp-mirror-editor-quote-color);
}
.cm-s-jupyter span.cm-link {
  color: var(--jp-mirror-editor-link-color);
}
.cm-s-jupyter span.cm-error {
  color: var(--jp-mirror-editor-error-color);
}
.cm-s-jupyter span.cm-hr {
  color: #999;
}

.cm-s-jupyter span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}

.cm-s-jupyter .CodeMirror-activeline-background,
.cm-s-jupyter .CodeMirror-gutter {
  background-color: var(--jp-layout-color2);
}

/* Styles for shared cursors (remote cursor locations and selected ranges) */
.jp-CodeMirrorEditor .remote-caret {
  position: relative;
  border-left: 2px solid black;
  margin-left: -1px;
  margin-right: -1px;
  box-sizing: border-box;
}

.jp-CodeMirrorEditor .remote-caret > div {
  white-space: nowrap;
  position: absolute;
  top: -1.15em;
  padding-bottom: 0.05em;
  left: -2px;
  font-size: 0.95em;
  background-color: rgb(250, 129, 0);
  font-family: var(--jp-ui-font-family);
  font-weight: bold;
  line-height: normal;
  user-select: none;
  color: white;
  padding-left: 2px;
  padding-right: 2px;
  z-index: 3;
  transition: opacity 0.3s ease-in-out;
}

.jp-CodeMirrorEditor .remote-caret.hide-name > div {
  transition-delay: 0.7s;
  opacity: 0;
}

.jp-CodeMirrorEditor .remote-caret:hover > div {
  opacity: 1;
  transition-delay: 0s;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| RenderedText
|----------------------------------------------------------------------------*/

:root {
  /* This is the padding value to fill the gaps between lines containing spans with background color. */
  --jp-private-code-span-padding: calc(
    (var(--jp-code-line-height) - 1) * var(--jp-code-font-size) / 2
  );
}

.jp-RenderedText {
  text-align: left;
  padding-left: var(--jp-code-padding);
  line-height: var(--jp-code-line-height);
  font-family: var(--jp-code-font-family);
}

.jp-RenderedText pre,
.jp-RenderedJavaScript pre,
.jp-RenderedHTMLCommon pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
  border: none;
  margin: 0px;
  padding: 0px;
}

.jp-RenderedText pre a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* console foregrounds and backgrounds */
.jp-RenderedText pre .ansi-black-fg {
  color: #3e424d;
}
.jp-RenderedText pre .ansi-red-fg {
  color: #e75c58;
}
.jp-RenderedText pre .ansi-green-fg {
  color: #00a250;
}
.jp-RenderedText pre .ansi-yellow-fg {
  color: #ddb62b;
}
.jp-RenderedText pre .ansi-blue-fg {
  color: #208ffb;
}
.jp-RenderedText pre .ansi-magenta-fg {
  color: #d160c4;
}
.jp-RenderedText pre .ansi-cyan-fg {
  color: #60c6c8;
}
.jp-RenderedText pre .ansi-white-fg {
  color: #c5c1b4;
}

.jp-RenderedText pre .ansi-black-bg {
  background-color: #3e424d;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-red-bg {
  background-color: #e75c58;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-green-bg {
  background-color: #00a250;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-yellow-bg {
  background-color: #ddb62b;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-blue-bg {
  background-color: #208ffb;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-magenta-bg {
  background-color: #d160c4;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-cyan-bg {
  background-color: #60c6c8;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-white-bg {
  background-color: #c5c1b4;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-black-intense-fg {
  color: #282c36;
}
.jp-RenderedText pre .ansi-red-intense-fg {
  color: #b22b31;
}
.jp-RenderedText pre .ansi-green-intense-fg {
  color: #007427;
}
.jp-RenderedText pre .ansi-yellow-intense-fg {
  color: #b27d12;
}
.jp-RenderedText pre .ansi-blue-intense-fg {
  color: #0065ca;
}
.jp-RenderedText pre .ansi-magenta-intense-fg {
  color: #a03196;
}
.jp-RenderedText pre .ansi-cyan-intense-fg {
  color: #258f8f;
}
.jp-RenderedText pre .ansi-white-intense-fg {
  color: #a1a6b2;
}

.jp-RenderedText pre .ansi-black-intense-bg {
  background-color: #282c36;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-red-intense-bg {
  background-color: #b22b31;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-green-intense-bg {
  background-color: #007427;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-yellow-intense-bg {
  background-color: #b27d12;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-blue-intense-bg {
  background-color: #0065ca;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-magenta-intense-bg {
  background-color: #a03196;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-cyan-intense-bg {
  background-color: #258f8f;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-white-intense-bg {
  background-color: #a1a6b2;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-default-inverse-fg {
  color: var(--jp-ui-inverse-font-color0);
}
.jp-RenderedText pre .ansi-default-inverse-bg {
  background-color: var(--jp-inverse-layout-color0);
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-bold {
  font-weight: bold;
}
.jp-RenderedText pre .ansi-underline {
  text-decoration: underline;
}

.jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
  background: var(--jp-rendermime-error-background);
  padding-top: var(--jp-code-padding);
}

/*-----------------------------------------------------------------------------
| RenderedLatex
|----------------------------------------------------------------------------*/

.jp-RenderedLatex {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
}

/* Left-justify outputs.*/
.jp-OutputArea-output.jp-RenderedLatex {
  padding: var(--jp-code-padding);
  text-align: left;
}

/*-----------------------------------------------------------------------------
| RenderedHTML
|----------------------------------------------------------------------------*/

.jp-RenderedHTMLCommon {
  color: var(--jp-content-font-color1);
  font-family: var(--jp-content-font-family);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
  /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
  padding-right: 20px;
}

.jp-RenderedHTMLCommon em {
  font-style: italic;
}

.jp-RenderedHTMLCommon strong {
  font-weight: bold;
}

.jp-RenderedHTMLCommon u {
  text-decoration: underline;
}

.jp-RenderedHTMLCommon a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* Headings */

.jp-RenderedHTMLCommon h1,
.jp-RenderedHTMLCommon h2,
.jp-RenderedHTMLCommon h3,
.jp-RenderedHTMLCommon h4,
.jp-RenderedHTMLCommon h5,
.jp-RenderedHTMLCommon h6 {
  line-height: var(--jp-content-heading-line-height);
  font-weight: var(--jp-content-heading-font-weight);
  font-style: normal;
  margin: var(--jp-content-heading-margin-top) 0
    var(--jp-content-heading-margin-bottom) 0;
}

.jp-RenderedHTMLCommon h1:first-child,
.jp-RenderedHTMLCommon h2:first-child,
.jp-RenderedHTMLCommon h3:first-child,
.jp-RenderedHTMLCommon h4:first-child,
.jp-RenderedHTMLCommon h5:first-child,
.jp-RenderedHTMLCommon h6:first-child {
  margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
}

.jp-RenderedHTMLCommon h1:last-child,
.jp-RenderedHTMLCommon h2:last-child,
.jp-RenderedHTMLCommon h3:last-child,
.jp-RenderedHTMLCommon h4:last-child,
.jp-RenderedHTMLCommon h5:last-child,
.jp-RenderedHTMLCommon h6:last-child {
  margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
}

.jp-RenderedHTMLCommon h1 {
  font-size: var(--jp-content-font-size5);
}

.jp-RenderedHTMLCommon h2 {
  font-size: var(--jp-content-font-size4);
}

.jp-RenderedHTMLCommon h3 {
  font-size: var(--jp-content-font-size3);
}

.jp-RenderedHTMLCommon h4 {
  font-size: var(--jp-content-font-size2);
}

.jp-RenderedHTMLCommon h5 {
  font-size: var(--jp-content-font-size1);
}

.jp-RenderedHTMLCommon h6 {
  font-size: var(--jp-content-font-size0);
}

/* Lists */

.jp-RenderedHTMLCommon ul:not(.list-inline),
.jp-RenderedHTMLCommon ol:not(.list-inline) {
  padding-left: 2em;
}

.jp-RenderedHTMLCommon ul {
  list-style: disc;
}

.jp-RenderedHTMLCommon ul ul {
  list-style: square;
}

.jp-RenderedHTMLCommon ul ul ul {
  list-style: circle;
}

.jp-RenderedHTMLCommon ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol ol {
  list-style: upper-alpha;
}

.jp-RenderedHTMLCommon ol ol ol {
  list-style: lower-alpha;
}

.jp-RenderedHTMLCommon ol ol ol ol {
  list-style: lower-roman;
}

.jp-RenderedHTMLCommon ol ol ol ol ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol,
.jp-RenderedHTMLCommon ul {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon ul ul,
.jp-RenderedHTMLCommon ul ol,
.jp-RenderedHTMLCommon ol ul,
.jp-RenderedHTMLCommon ol ol {
  margin-bottom: 0em;
}

.jp-RenderedHTMLCommon hr {
  color: var(--jp-border-color2);
  background-color: var(--jp-border-color1);
  margin-top: 1em;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon > pre {
  margin: 1.5em 2em;
}

.jp-RenderedHTMLCommon pre,
.jp-RenderedHTMLCommon code {
  border: 0;
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  line-height: var(--jp-code-line-height);
  padding: 0;
  white-space: pre-wrap;
}

.jp-RenderedHTMLCommon :not(pre) > code {
  background-color: var(--jp-layout-color2);
  padding: 1px 5px;
}

/* Tables */

.jp-RenderedHTMLCommon table {
  border-collapse: collapse;
  border-spacing: 0;
  border: none;
  color: var(--jp-ui-font-color1);
  font-size: 12px;
  table-layout: fixed;
  margin-left: auto;
  margin-right: auto;
}

.jp-RenderedHTMLCommon thead {
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  vertical-align: bottom;
}

.jp-RenderedHTMLCommon td,
.jp-RenderedHTMLCommon th,
.jp-RenderedHTMLCommon tr {
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}

.jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
.jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
  max-width: none;
}

:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
  text-align: right;
}

.jp-RenderedHTMLCommon th {
  font-weight: bold;
}

.jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
  background: var(--jp-layout-color0);
}

.jp-RenderedHTMLCommon tbody tr:nth-child(even) {
  background: var(--jp-rendermime-table-row-background);
}

.jp-RenderedHTMLCommon tbody tr:hover {
  background: var(--jp-rendermime-table-row-hover-background);
}

.jp-RenderedHTMLCommon table {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon p {
  text-align: left;
  margin: 0px;
}

.jp-RenderedHTMLCommon p {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon img {
  -moz-force-broken-image-icon: 1;
}

/* Restrict to direct children as other images could be nested in other content. */
.jp-RenderedHTMLCommon > img {
  display: block;
  margin-left: 0;
  margin-right: 0;
  margin-bottom: 1em;
}

/* Change color behind transparent images if they need it... */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
  background-color: var(--jp-inverse-layout-color1);
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
  background-color: var(--jp-inverse-layout-color1);
}
/* ...or leave it untouched if they don't */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-dark-background {
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-light-background {
}

.jp-RenderedHTMLCommon img,
.jp-RenderedImage img,
.jp-RenderedHTMLCommon svg,
.jp-RenderedSVG svg {
  max-width: 100%;
  height: auto;
}

.jp-RenderedHTMLCommon img.jp-mod-unconfined,
.jp-RenderedImage img.jp-mod-unconfined,
.jp-RenderedHTMLCommon svg.jp-mod-unconfined,
.jp-RenderedSVG svg.jp-mod-unconfined {
  max-width: none;
}

.jp-RenderedHTMLCommon .alert {
  padding: var(--jp-notebook-padding);
  border: var(--jp-border-width) solid transparent;
  border-radius: var(--jp-border-radius);
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon .alert-info {
  color: var(--jp-info-color0);
  background-color: var(--jp-info-color3);
  border-color: var(--jp-info-color2);
}
.jp-RenderedHTMLCommon .alert-info hr {
  border-color: var(--jp-info-color3);
}
.jp-RenderedHTMLCommon .alert-info > p:last-child,
.jp-RenderedHTMLCommon .alert-info > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-warning {
  color: var(--jp-warn-color0);
  background-color: var(--jp-warn-color3);
  border-color: var(--jp-warn-color2);
}
.jp-RenderedHTMLCommon .alert-warning hr {
  border-color: var(--jp-warn-color3);
}
.jp-RenderedHTMLCommon .alert-warning > p:last-child,
.jp-RenderedHTMLCommon .alert-warning > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-success {
  color: var(--jp-success-color0);
  background-color: var(--jp-success-color3);
  border-color: var(--jp-success-color2);
}
.jp-RenderedHTMLCommon .alert-success hr {
  border-color: var(--jp-success-color3);
}
.jp-RenderedHTMLCommon .alert-success > p:last-child,
.jp-RenderedHTMLCommon .alert-success > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-danger {
  color: var(--jp-error-color0);
  background-color: var(--jp-error-color3);
  border-color: var(--jp-error-color2);
}
.jp-RenderedHTMLCommon .alert-danger hr {
  border-color: var(--jp-error-color3);
}
.jp-RenderedHTMLCommon .alert-danger > p:last-child,
.jp-RenderedHTMLCommon .alert-danger > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon blockquote {
  margin: 1em 2em;
  padding: 0 1em;
  border-left: 5px solid var(--jp-border-color2);
}

a.jp-InternalAnchorLink {
  visibility: hidden;
  margin-left: 8px;
  color: var(--md-blue-800);
}

h1:hover .jp-InternalAnchorLink,
h2:hover .jp-InternalAnchorLink,
h3:hover .jp-InternalAnchorLink,
h4:hover .jp-InternalAnchorLink,
h5:hover .jp-InternalAnchorLink,
h6:hover .jp-InternalAnchorLink {
  visibility: visible;
}

.jp-RenderedHTMLCommon kbd {
  background-color: var(--jp-rendermime-table-row-background);
  border: 1px solid var(--jp-border-color0);
  border-bottom-color: var(--jp-border-color2);
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
  display: inline-block;
  font-size: 0.8em;
  line-height: 1em;
  padding: 0.2em 0.5em;
}

/* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
 * At the bottom of cells this is a bit too much as there is also spacing
 * between cells. Going all the way to 0 gets too tight between markdown and
 * code cells.
 */
.jp-RenderedHTMLCommon > *:last-child {
  margin-bottom: 0.5em;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MimeDocument {
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-filebrowser-button-height: 28px;
  --jp-private-filebrowser-button-width: 48px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FileBrowser {
  display: flex;
  flex-direction: column;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  border-bottom: none;
  height: auto;
  margin: var(--jp-toolbar-header-margin);
  box-shadow: none;
}

.jp-BreadCrumbs {
  flex: 0 0 auto;
  margin: 8px 12px 8px 12px;
}

.jp-BreadCrumbs-item {
  margin: 0px 2px;
  padding: 0px 2px;
  border-radius: var(--jp-border-radius);
  cursor: pointer;
}

.jp-BreadCrumbs-item:hover {
  background-color: var(--jp-layout-color2);
}

.jp-BreadCrumbs-item:first-child {
  margin-left: 0px;
}

.jp-BreadCrumbs-item.jp-mod-dropTarget {
  background-color: var(--jp-brand-color2);
  opacity: 0.7;
}

/*-----------------------------------------------------------------------------
| Buttons
|----------------------------------------------------------------------------*/

.jp-FileBrowser-toolbar.jp-Toolbar {
  padding: 0px;
  margin: 8px 12px 0px 12px;
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  justify-content: flex-start;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-Toolbar-item {
  flex: 0 0 auto;
  padding-left: 0px;
  padding-right: 2px;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-ToolbarButtonComponent {
  width: 40px;
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent {
  width: 72px;
  background: var(--jp-brand-color1);
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent:focus-visible {
  background-color: var(--jp-brand-color0);
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent
  .jp-icon3 {
  fill: white;
}

/*-----------------------------------------------------------------------------
| Other styles
|----------------------------------------------------------------------------*/

.jp-FileDialog.jp-mod-conflict input {
  color: var(--jp-error-color1);
}

.jp-FileDialog .jp-new-name-title {
  margin-top: 12px;
}

.jp-LastModified-hidden {
  display: none;
}

.jp-FileBrowser-filterBox {
  padding: 0px;
  flex: 0 0 auto;
  margin: 8px 12px 0px 12px;
}

/*-----------------------------------------------------------------------------
| DirListing
|----------------------------------------------------------------------------*/

.jp-DirListing {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  outline: 0;
}

.jp-DirListing:focus-visible {
  border: 1px solid var(--jp-brand-color1);
}

.jp-DirListing-header {
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  overflow: hidden;
  border-top: var(--jp-border-width) solid var(--jp-border-color2);
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
}

.jp-DirListing-headerItem {
  padding: 4px 12px 2px 12px;
  font-weight: 500;
}

.jp-DirListing-headerItem:hover {
  background: var(--jp-layout-color2);
}

.jp-DirListing-headerItem.jp-id-name {
  flex: 1 0 84px;
}

.jp-DirListing-headerItem.jp-id-modified {
  flex: 0 0 112px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-id-narrow {
  display: none;
  flex: 0 0 5px;
  padding: 4px 4px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
  color: var(--jp-border-color2);
}

.jp-DirListing-narrow .jp-id-narrow {
  display: block;
}

.jp-DirListing-narrow .jp-id-modified,
.jp-DirListing-narrow .jp-DirListing-itemModified {
  display: none;
}

.jp-DirListing-headerItem.jp-mod-selected {
  font-weight: 600;
}

/* increase specificity to override bundled default */
.jp-DirListing-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-DirListing-content mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.jp-DirListing-content .jp-DirListing-item.jp-mod-selected mark {
  color: var(--jp-ui-inverse-font-color0);
}

/* Style the directory listing content when a user drops a file to upload */
.jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
  outline: 5px dashed rgba(128, 128, 128, 0.5);
  outline-offset: -10px;
  cursor: copy;
}

.jp-DirListing-item {
  display: flex;
  flex-direction: row;
  padding: 4px 12px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-DirListing-item[data-is-dot] {
  opacity: 75%;
}

.jp-DirListing-item.jp-mod-selected {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.jp-DirListing-item.jp-mod-dropTarget {
  background: var(--jp-brand-color3);
}

.jp-DirListing-item:hover:not(.jp-mod-selected) {
  background: var(--jp-layout-color2);
}

.jp-DirListing-itemIcon {
  flex: 0 0 20px;
  margin-right: 4px;
}

.jp-DirListing-itemText {
  flex: 1 0 64px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  user-select: none;
}

.jp-DirListing-itemModified {
  flex: 0 0 125px;
  text-align: right;
}

.jp-DirListing-editor {
  flex: 1 0 64px;
  outline: none;
  border: none;
}

.jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon:before {
  color: var(--jp-success-color1);
  content: '\25CF';
  font-size: 8px;
  position: absolute;
  left: -8px;
}

.jp-DirListing-item.jp-mod-running.jp-mod-selected
  .jp-DirListing-itemIcon:before {
  color: var(--jp-ui-inverse-font-color1);
}

.jp-DirListing-item.lm-mod-drag-image,
.jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
  font-size: var(--jp-ui-font-size1);
  padding-left: 4px;
  margin-left: 4px;
  width: 160px;
  background-color: var(--jp-ui-inverse-font-color2);
  box-shadow: var(--jp-elevation-z2);
  border-radius: 0px;
  color: var(--jp-ui-font-color1);
  transform: translateX(-40%) translateY(-58%);
}

.jp-DirListing-deadSpace {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-Document {
  min-width: 120px;
  min-height: 120px;
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
}

/*-----------------------------------------------------------------------------
| Main OutputArea
| OutputArea has a list of Outputs
|----------------------------------------------------------------------------*/

.jp-OutputArea {
  overflow-y: auto;
}

.jp-OutputArea-child {
  display: flex;
  flex-direction: row;
}

body[data-format='mobile'] .jp-OutputArea-child {
  flex-direction: column;
}

.jp-OutputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-outprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

body[data-format='mobile'] .jp-OutputPrompt {
  flex: 0 0 auto;
  text-align: left;
}

.jp-OutputArea-output {
  height: auto;
  overflow: auto;
  user-select: text;
  -moz-user-select: text;
  -webkit-user-select: text;
  -ms-user-select: text;
}

.jp-OutputArea-child .jp-OutputArea-output {
  flex-grow: 1;
  flex-shrink: 1;
}

body[data-format='mobile'] .jp-OutputArea-child .jp-OutputArea-output {
  margin-left: var(--jp-notebook-padding);
}

/**
 * Isolated output.
 */
.jp-OutputArea-output.jp-mod-isolated {
  width: 100%;
  display: block;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
  position: relative;
}

body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/* pre */

.jp-OutputArea-output pre {
  border: none;
  margin: 0px;
  padding: 0px;
  overflow-x: auto;
  overflow-y: auto;
  word-break: break-all;
  word-wrap: break-word;
  white-space: pre-wrap;
}

/* tables */

.jp-OutputArea-output.jp-RenderedHTMLCommon table {
  margin-left: 0;
  margin-right: 0;
}

/* description lists */

.jp-OutputArea-output dl,
.jp-OutputArea-output dt,
.jp-OutputArea-output dd {
  display: block;
}

.jp-OutputArea-output dl {
  width: 100%;
  overflow: hidden;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dt {
  font-weight: bold;
  float: left;
  width: 20%;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dd {
  float: left;
  width: 80%;
  padding: 0;
  margin: 0;
}

/* Hide the gutter in case of
 *  - nested output areas (e.g. in the case of output widgets)
 *  - mirrored output areas
 */
.jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
  display: none;
}

/*-----------------------------------------------------------------------------
| executeResult is added to any Output-result for the display of the object
| returned by a cell
|----------------------------------------------------------------------------*/

.jp-OutputArea-output.jp-OutputArea-executeResult {
  margin-left: 0px;
  flex: 1 1 auto;
}

/* Text output with the Out[] prompt needs a top padding to match the
 * alignment of the Out[] prompt itself.
 */
.jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
  padding-top: var(--jp-code-padding);
  border-top: var(--jp-border-width) solid transparent;
}

/*-----------------------------------------------------------------------------
| The Stdin output
|----------------------------------------------------------------------------*/

.jp-OutputArea-stdin {
  line-height: var(--jp-code-line-height);
  padding-top: var(--jp-code-padding);
  display: flex;
}

.jp-Stdin-prompt {
  color: var(--jp-content-font-color0);
  padding-right: var(--jp-code-padding);
  vertical-align: baseline;
  flex: 0 0 auto;
}

.jp-Stdin-input {
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  color: inherit;
  background-color: inherit;
  width: 42%;
  min-width: 200px;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
  flex: 0 0 70%;
}

.jp-Stdin-input:focus {
  box-shadow: none;
}

/*-----------------------------------------------------------------------------
| Output Area View
|----------------------------------------------------------------------------*/

.jp-LinkedOutputView .jp-OutputArea {
  height: 100%;
  display: block;
}

.jp-LinkedOutputView .jp-OutputArea-output:only-child {
  height: 100%;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapser {
  flex: 0 0 var(--jp-cell-collapser-width);
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
  border-radius: var(--jp-border-radius);
  opacity: 1;
}

.jp-Collapser-child {
  display: block;
  width: 100%;
  box-sizing: border-box;
  /* height: 100% doesn't work because the height of its parent is computed from content */
  position: absolute;
  top: 0px;
  bottom: 0px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Header/Footer
|----------------------------------------------------------------------------*/

/* Hidden by zero height by default */
.jp-CellHeader,
.jp-CellFooter {
  height: 0px;
  width: 100%;
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Input
|----------------------------------------------------------------------------*/

/* All input areas */
.jp-InputArea {
  display: flex;
  flex-direction: row;
  overflow: hidden;
}

body[data-format='mobile'] .jp-InputArea {
  flex-direction: column;
}

.jp-InputArea-editor {
  flex: 1 1 auto;
  overflow: hidden;
}

.jp-InputArea-editor {
  /* This is the non-active, default styling */
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0px;
  background: var(--jp-cell-editor-background);
}

body[data-format='mobile'] .jp-InputArea-editor {
  margin-left: var(--jp-notebook-padding);
}

.jp-InputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-inprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  opacity: var(--jp-cell-prompt-opacity);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

body[data-format='mobile'] .jp-InputPrompt {
  flex: 0 0 auto;
  text-align: left;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Placeholder {
  display: flex;
  flex-direction: row;
  flex: 1 1 auto;
}

.jp-Placeholder-prompt {
  box-sizing: border-box;
}

.jp-Placeholder-content {
  flex: 1 1 auto;
  border: none;
  background: transparent;
  height: 20px;
  box-sizing: border-box;
}

.jp-Placeholder-content .jp-MoreHorizIcon {
  width: 32px;
  height: 16px;
  border: 1px solid transparent;
  border-radius: var(--jp-border-radius);
}

.jp-Placeholder-content .jp-MoreHorizIcon:hover {
  border: 1px solid var(--jp-border-color1);
  box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
  background-color: var(--jp-layout-color0);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-cell-scrolling-output-offset: 5px;
}

/*-----------------------------------------------------------------------------
| Cell
|----------------------------------------------------------------------------*/

.jp-Cell {
  padding: var(--jp-cell-padding);
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Common input/output
|----------------------------------------------------------------------------*/

.jp-Cell-inputWrapper,
.jp-Cell-outputWrapper {
  display: flex;
  flex-direction: row;
  padding: 0px;
  margin: 0px;
  /* Added to reveal the box-shadow on the input and output collapsers. */
  overflow: visible;
}

/* Only input/output areas inside cells */
.jp-Cell-inputArea,
.jp-Cell-outputArea {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Collapser
|----------------------------------------------------------------------------*/

/* Make the output collapser disappear when there is not output, but do so
 * in a manner that leaves it in the layout and preserves its width.
 */
.jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
  border: none !important;
  background: transparent !important;
}

.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
  min-height: var(--jp-cell-collapser-min-height);
}

/*-----------------------------------------------------------------------------
| Output
|----------------------------------------------------------------------------*/

/* Put a space between input and output when there IS output */
.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
  margin-top: 5px;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
  overflow-y: auto;
  max-height: 200px;
  box-shadow: inset 0 0 6px 2px rgba(0, 0, 0, 0.3);
  margin-left: var(--jp-private-cell-scrolling-output-offset);
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  flex: 0 0
    calc(
      var(--jp-cell-prompt-width) -
        var(--jp-private-cell-scrolling-output-offset)
    );
}

/*-----------------------------------------------------------------------------
| CodeCell
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| MarkdownCell
|----------------------------------------------------------------------------*/

.jp-MarkdownOutput {
  flex: 1 1 auto;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: var(--jp-code-padding);
}

.jp-MarkdownOutput.jp-RenderedHTMLCommon {
  overflow: auto;
}

.jp-showHiddenCellsButton {
  margin-left: calc(var(--jp-cell-prompt-width) + 2 * var(--jp-code-padding));
  margin-top: var(--jp-code-padding);
  border: 1px solid var(--jp-border-color2);
  background-color: var(--jp-border-color3) !important;
  color: var(--jp-content-font-color0) !important;
}

.jp-showHiddenCellsButton:hover {
  background-color: var(--jp-border-color2) !important;
}

.jp-collapseHeadingButton {
  display: none;
}

.jp-MarkdownCell:hover .jp-collapseHeadingButton {
  display: flex;
  min-height: var(--jp-cell-collapser-min-height);
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-NotebookPanel-toolbar {
  padding: 2px;
}

.jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
  border: none;
  box-shadow: none;
}

.jp-Notebook-toolbarCellTypeDropdown select {
  height: 24px;
  font-size: var(--jp-ui-font-size1);
  line-height: 14px;
  border-radius: 0;
  display: block;
}

.jp-Notebook-toolbarCellTypeDropdown span {
  top: 5px !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-notebook-dragImage-width: 304px;
  --jp-private-notebook-dragImage-height: 36px;
  --jp-private-notebook-selected-color: var(--md-blue-400);
  --jp-private-notebook-active-color: var(--md-green-400);
}

/*-----------------------------------------------------------------------------
| Imports
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Notebook
|----------------------------------------------------------------------------*/

.jp-NotebookPanel {
  display: block;
  height: 100%;
}

.jp-NotebookPanel.jp-Document {
  min-width: 240px;
  min-height: 120px;
}

.jp-Notebook {
  padding: var(--jp-notebook-padding);
  outline: none;
  overflow: auto;
  background: var(--jp-layout-color0);
}

.jp-Notebook.jp-mod-scrollPastEnd::after {
  display: block;
  content: '';
  min-height: var(--jp-notebook-scroll-padding);
}

.jp-MainAreaWidget-ContainStrict .jp-Notebook * {
  contain: strict;
}

.jp-Notebook-render * {
  contain: none !important;
}

.jp-Notebook .jp-Cell {
  overflow: visible;
}

.jp-Notebook .jp-Cell .jp-InputPrompt {
  cursor: move;
  float: left;
}

/*-----------------------------------------------------------------------------
| Notebook state related styling
|
| The notebook and cells each have states, here are the possibilities:
|
| - Notebook
|   - Command
|   - Edit
| - Cell
|   - None
|   - Active (only one can be active)
|   - Selected (the cells actions are applied to)
|   - Multiselected (when multiple selected, the cursor)
|   - No outputs
|----------------------------------------------------------------------------*/

/* Command or edit modes */

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

/* cell is active */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
  background: var(--jp-brand-color1);
}

/* cell is dirty */
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt {
  color: var(--jp-warn-color1);
}
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt:before {
  color: var(--jp-warn-color1);
  content: '•';
}

.jp-Notebook .jp-Cell.jp-mod-active.jp-mod-dirty .jp-Collapser {
  background: var(--jp-warn-color1);
}

/* collapser is hovered */
.jp-Notebook .jp-Cell .jp-Collapser:hover {
  box-shadow: var(--jp-elevation-z2);
  background: var(--jp-brand-color1);
  opacity: var(--jp-cell-collapser-not-active-hover-opacity);
}

/* cell is active and collapser is hovered */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/* Command mode */

.jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
  background: var(--jp-notebook-multiselected-color);
}

.jp-Notebook.jp-mod-commandMode
  .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
  background: transparent;
}

/* Edit mode */

.jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-cell-editor-active-background);
}

/*-----------------------------------------------------------------------------
| Notebook drag and drop
|----------------------------------------------------------------------------*/

.jp-Notebook-cell.jp-mod-dropSource {
  opacity: 0.5;
}

.jp-Notebook-cell.jp-mod-dropTarget,
.jp-Notebook.jp-mod-commandMode
  .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
  border-top-color: var(--jp-private-notebook-selected-color);
  border-top-style: solid;
  border-top-width: 2px;
}

.jp-dragImage {
  display: block;
  flex-direction: row;
  width: var(--jp-private-notebook-dragImage-width);
  height: var(--jp-private-notebook-dragImage-height);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
  overflow: visible;
}

.jp-dragImage-singlePrompt {
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

.jp-dragImage .jp-dragImage-content {
  flex: 1 1 auto;
  z-index: 2;
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  line-height: var(--jp-code-line-height);
  padding: var(--jp-code-padding);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background-color);
  color: var(--jp-content-font-color3);
  text-align: left;
  margin: 4px 4px 4px 0px;
}

.jp-dragImage .jp-dragImage-prompt {
  flex: 0 0 auto;
  min-width: 36px;
  color: var(--jp-cell-inprompt-font-color);
  padding: var(--jp-code-padding);
  padding-left: 12px;
  font-family: var(--jp-cell-prompt-font-family);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: 1.9;
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
}

.jp-dragImage-multipleBack {
  z-index: -1;
  position: absolute;
  height: 32px;
  width: 300px;
  top: 8px;
  left: 8px;
  background: var(--jp-layout-color2);
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

/*-----------------------------------------------------------------------------
| Cell toolbar
|----------------------------------------------------------------------------*/

.jp-NotebookTools {
  display: block;
  min-width: var(--jp-sidebar-min-width);
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  overflow: auto;
}

.jp-NotebookTools-tool {
  padding: 0px 12px 0 12px;
}

.jp-ActiveCellTool {
  padding: 12px;
  background-color: var(--jp-layout-color1);
  border-top: none !important;
}

.jp-ActiveCellTool .jp-InputArea-prompt {
  flex: 0 0 auto;
  padding-left: 0px;
}

.jp-ActiveCellTool .jp-InputArea-editor {
  flex: 1 1 auto;
  background: var(--jp-cell-editor-background);
  border-color: var(--jp-cell-editor-border-color);
}

.jp-ActiveCellTool .jp-InputArea-editor .CodeMirror {
  background: transparent;
}

.jp-MetadataEditorTool {
  flex-direction: column;
  padding: 12px 0px 12px 0px;
}

.jp-RankedPanel > :not(:first-child) {
  margin-top: 12px;
}

.jp-KeySelector select.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: var(--jp-border-width) solid var(--jp-border-color1);
}

.jp-KeySelector label,
.jp-MetadataEditorTool label {
  line-height: 1.4;
}

.jp-NotebookTools .jp-select-wrapper {
  margin-top: 4px;
  margin-bottom: 0px;
}

.jp-NotebookTools .jp-Collapse {
  margin-top: 16px;
}

/*-----------------------------------------------------------------------------
| Presentation Mode (.jp-mod-presentationMode)
|----------------------------------------------------------------------------*/

.jp-mod-presentationMode .jp-Notebook {
  --jp-content-font-size1: var(--jp-content-presentation-font-size1);
  --jp-code-font-size: var(--jp-code-presentation-font-size);
}

.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
  flex: 0 0 110px;
}

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Cell-Placeholder {
  padding-left: 55px;
}

.jp-Cell-Placeholder-wrapper {
  background: #fff;
  border: 1px solid;
  border-color: #e5e6e9 #dfe0e4 #d0d1d5;
  border-radius: 4px;
  -webkit-border-radius: 4px;
  margin: 10px 15px;
}

.jp-Cell-Placeholder-wrapper-inner {
  padding: 15px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body {
  background-repeat: repeat;
  background-size: 50% auto;
}

.jp-Cell-Placeholder-wrapper-body div {
  background: #f6f7f8;
  background-image: -webkit-linear-gradient(
    left,
    #f6f7f8 0%,
    #edeef1 20%,
    #f6f7f8 40%,
    #f6f7f8 100%
  );
  background-repeat: no-repeat;
  background-size: 800px 104px;
  height: 104px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body div {
  position: absolute;
  right: 15px;
  left: 15px;
  top: 15px;
}

div.jp-Cell-Placeholder-h1 {
  top: 20px;
  height: 20px;
  left: 15px;
  width: 150px;
}

div.jp-Cell-Placeholder-h2 {
  left: 15px;
  top: 50px;
  height: 10px;
  width: 100px;
}

div.jp-Cell-Placeholder-content-1,
div.jp-Cell-Placeholder-content-2,
div.jp-Cell-Placeholder-content-3 {
  left: 15px;
  right: 15px;
  height: 10px;
}

div.jp-Cell-Placeholder-content-1 {
  top: 100px;
}

div.jp-Cell-Placeholder-content-2 {
  top: 120px;
}

div.jp-Cell-Placeholder-content-3 {
  top: 140px;
}

</style>

    <style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
The following CSS variables define the main, public API for styling JupyterLab.
These variables should be used by all plugins wherever possible. In other
words, plugins should not define custom colors, sizes, etc unless absolutely
necessary. This enables users to change the visual theme of JupyterLab
by changing these variables.

Many variables appear in an ordered sequence (0,1,2,3). These sequences
are designed to work well together, so for example, `--jp-border-color1` should
be used with `--jp-layout-color1`. The numbers have the following meanings:

* 0: super-primary, reserved for special emphasis
* 1: primary, most important under normal situations
* 2: secondary, next most important under normal situations
* 3: tertiary, next most important under normal situations

Throughout JupyterLab, we are mostly following principles from Google's
Material Design when selecting colors. We are not, however, following
all of MD as it is not optimized for dense, information rich UIs.
*/

:root {
  /* Elevation
   *
   * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
   *
   * https://github.com/material-components/material-components-web
   * https://material-components-web.appspot.com/elevation.html
   */

  --jp-shadow-base-lightness: 0;
  --jp-shadow-umbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.2
  );
  --jp-shadow-penumbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.14
  );
  --jp-shadow-ambient-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.12
  );
  --jp-elevation-z0: none;
  --jp-elevation-z1: 0px 2px 1px -1px var(--jp-shadow-umbra-color),
    0px 1px 1px 0px var(--jp-shadow-penumbra-color),
    0px 1px 3px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z2: 0px 3px 1px -2px var(--jp-shadow-umbra-color),
    0px 2px 2px 0px var(--jp-shadow-penumbra-color),
    0px 1px 5px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z4: 0px 2px 4px -1px var(--jp-shadow-umbra-color),
    0px 4px 5px 0px var(--jp-shadow-penumbra-color),
    0px 1px 10px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z6: 0px 3px 5px -1px var(--jp-shadow-umbra-color),
    0px 6px 10px 0px var(--jp-shadow-penumbra-color),
    0px 1px 18px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z8: 0px 5px 5px -3px var(--jp-shadow-umbra-color),
    0px 8px 10px 1px var(--jp-shadow-penumbra-color),
    0px 3px 14px 2px var(--jp-shadow-ambient-color);
  --jp-elevation-z12: 0px 7px 8px -4px var(--jp-shadow-umbra-color),
    0px 12px 17px 2px var(--jp-shadow-penumbra-color),
    0px 5px 22px 4px var(--jp-shadow-ambient-color);
  --jp-elevation-z16: 0px 8px 10px -5px var(--jp-shadow-umbra-color),
    0px 16px 24px 2px var(--jp-shadow-penumbra-color),
    0px 6px 30px 5px var(--jp-shadow-ambient-color);
  --jp-elevation-z20: 0px 10px 13px -6px var(--jp-shadow-umbra-color),
    0px 20px 31px 3px var(--jp-shadow-penumbra-color),
    0px 8px 38px 7px var(--jp-shadow-ambient-color);
  --jp-elevation-z24: 0px 11px 15px -7px var(--jp-shadow-umbra-color),
    0px 24px 38px 3px var(--jp-shadow-penumbra-color),
    0px 9px 46px 8px var(--jp-shadow-ambient-color);

  /* Borders
   *
   * The following variables, specify the visual styling of borders in JupyterLab.
   */

  --jp-border-width: 1px;
  --jp-border-color0: var(--md-grey-400);
  --jp-border-color1: var(--md-grey-400);
  --jp-border-color2: var(--md-grey-300);
  --jp-border-color3: var(--md-grey-200);
  --jp-border-radius: 2px;

  /* UI Fonts
   *
   * The UI font CSS variables are used for the typography all of the JupyterLab
   * user interface elements that are not directly user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-ui-font-scale-factor: 1.2;
  --jp-ui-font-size0: 0.83333em;
  --jp-ui-font-size1: 13px; /* Base font size */
  --jp-ui-font-size2: 1.2em;
  --jp-ui-font-size3: 1.44em;

  --jp-ui-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica,
    Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';

  /*
   * Use these font colors against the corresponding main layout colors.
   * In a light theme, these go from dark to light.
   */

  /* Defaults use Material Design specification */
  --jp-ui-font-color0: rgba(0, 0, 0, 1);
  --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
  --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
  --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

  /*
   * Use these against the brand/accent/warn/error colors.
   * These will typically go from light to darker, in both a dark and light theme.
   */

  --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
  --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

  /* Content Fonts
   *
   * Content font variables are used for typography of user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-content-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-content-line-height: 1.6;
  --jp-content-font-scale-factor: 1.2;
  --jp-content-font-size0: 0.83333em;
  --jp-content-font-size1: 14px; /* Base font size */
  --jp-content-font-size2: 1.2em;
  --jp-content-font-size3: 1.44em;
  --jp-content-font-size4: 1.728em;
  --jp-content-font-size5: 2.0736em;

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-content-presentation-font-size1: 17px;

  --jp-content-heading-line-height: 1;
  --jp-content-heading-margin-top: 1.2em;
  --jp-content-heading-margin-bottom: 0.8em;
  --jp-content-heading-font-weight: 500;

  /* Defaults use Material Design specification */
  --jp-content-font-color0: rgba(0, 0, 0, 1);
  --jp-content-font-color1: rgba(0, 0, 0, 0.87);
  --jp-content-font-color2: rgba(0, 0, 0, 0.54);
  --jp-content-font-color3: rgba(0, 0, 0, 0.38);

  --jp-content-link-color: var(--md-blue-700);

  --jp-content-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';

  /*
   * Code Fonts
   *
   * Code font variables are used for typography of code and other monospaces content.
   */

  --jp-code-font-size: 13px;
  --jp-code-line-height: 1.3077; /* 17px for 13px base */
  --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
  --jp-code-font-family-default: Menlo, Consolas, 'DejaVu Sans Mono', monospace;
  --jp-code-font-family: var(--jp-code-font-family-default);

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-code-presentation-font-size: 16px;

  /* may need to tweak cursor width if you change font size */
  --jp-code-cursor-width0: 1.4px;
  --jp-code-cursor-width1: 2px;
  --jp-code-cursor-width2: 4px;

  /* Layout
   *
   * The following are the main layout colors use in JupyterLab. In a light
   * theme these would go from light to dark.
   */

  --jp-layout-color0: white;
  --jp-layout-color1: white;
  --jp-layout-color2: var(--md-grey-200);
  --jp-layout-color3: var(--md-grey-400);
  --jp-layout-color4: var(--md-grey-600);

  /* Inverse Layout
   *
   * The following are the inverse layout colors use in JupyterLab. In a light
   * theme these would go from dark to light.
   */

  --jp-inverse-layout-color0: #111111;
  --jp-inverse-layout-color1: var(--md-grey-900);
  --jp-inverse-layout-color2: var(--md-grey-800);
  --jp-inverse-layout-color3: var(--md-grey-700);
  --jp-inverse-layout-color4: var(--md-grey-600);

  /* Brand/accent */

  --jp-brand-color0: var(--md-blue-900);
  --jp-brand-color1: var(--md-blue-700);
  --jp-brand-color2: var(--md-blue-300);
  --jp-brand-color3: var(--md-blue-100);
  --jp-brand-color4: var(--md-blue-50);

  --jp-accent-color0: var(--md-green-900);
  --jp-accent-color1: var(--md-green-700);
  --jp-accent-color2: var(--md-green-300);
  --jp-accent-color3: var(--md-green-100);

  /* State colors (warn, error, success, info) */

  --jp-warn-color0: var(--md-orange-900);
  --jp-warn-color1: var(--md-orange-700);
  --jp-warn-color2: var(--md-orange-300);
  --jp-warn-color3: var(--md-orange-100);

  --jp-error-color0: var(--md-red-900);
  --jp-error-color1: var(--md-red-700);
  --jp-error-color2: var(--md-red-300);
  --jp-error-color3: var(--md-red-100);

  --jp-success-color0: var(--md-green-900);
  --jp-success-color1: var(--md-green-700);
  --jp-success-color2: var(--md-green-300);
  --jp-success-color3: var(--md-green-100);

  --jp-info-color0: var(--md-cyan-900);
  --jp-info-color1: var(--md-cyan-700);
  --jp-info-color2: var(--md-cyan-300);
  --jp-info-color3: var(--md-cyan-100);

  /* Cell specific styles */

  --jp-cell-padding: 5px;

  --jp-cell-collapser-width: 8px;
  --jp-cell-collapser-min-height: 20px;
  --jp-cell-collapser-not-active-hover-opacity: 0.6;

  --jp-cell-editor-background: var(--md-grey-100);
  --jp-cell-editor-border-color: var(--md-grey-300);
  --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-cell-editor-active-background: var(--jp-layout-color0);
  --jp-cell-editor-active-border-color: var(--jp-brand-color1);

  --jp-cell-prompt-width: 64px;
  --jp-cell-prompt-font-family: var(--jp-code-font-family-default);
  --jp-cell-prompt-letter-spacing: 0px;
  --jp-cell-prompt-opacity: 1;
  --jp-cell-prompt-not-active-opacity: 0.5;
  --jp-cell-prompt-not-active-font-color: var(--md-grey-700);
  /* A custom blend of MD grey and blue 600
   * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
  --jp-cell-inprompt-font-color: #307fc1;
  /* A custom blend of MD grey and orange 600
   * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
  --jp-cell-outprompt-font-color: #bf5b3d;

  /* Notebook specific styles */

  --jp-notebook-padding: 10px;
  --jp-notebook-select-background: var(--jp-layout-color1);
  --jp-notebook-multiselected-color: var(--md-blue-50);

  /* The scroll padding is calculated to fill enough space at the bottom of the
  notebook to show one single-line cell (with appropriate padding) at the top
  when the notebook is scrolled all the way to the bottom. We also subtract one
  pixel so that no scrollbar appears if we have just one single-line cell in the
  notebook. This padding is to enable a 'scroll past end' feature in a notebook.
  */
  --jp-notebook-scroll-padding: calc(
    100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
      var(--jp-code-padding) - var(--jp-cell-padding) - 1px
  );

  /* Rendermime styles */

  --jp-rendermime-error-background: #fdd;
  --jp-rendermime-table-row-background: var(--md-grey-100);
  --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

  /* Dialog specific styles */

  --jp-dialog-background: rgba(0, 0, 0, 0.25);

  /* Console specific styles */

  --jp-console-padding: 10px;

  /* Toolbar specific styles */

  --jp-toolbar-border-color: var(--jp-border-color1);
  --jp-toolbar-micro-height: 8px;
  --jp-toolbar-background: var(--jp-layout-color1);
  --jp-toolbar-box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.24);
  --jp-toolbar-header-margin: 4px 4px 0px 4px;
  --jp-toolbar-active-background: var(--md-grey-300);

  /* Statusbar specific styles */

  --jp-statusbar-height: 24px;

  /* Input field styles */

  --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-input-active-background: var(--jp-layout-color1);
  --jp-input-hover-background: var(--jp-layout-color1);
  --jp-input-background: var(--md-grey-100);
  --jp-input-border-color: var(--jp-border-color1);
  --jp-input-active-border-color: var(--jp-brand-color1);
  --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

  /* General editor styles */

  --jp-editor-selected-background: #d9d9d9;
  --jp-editor-selected-focused-background: #d7d4f0;
  --jp-editor-cursor-color: var(--jp-ui-font-color0);

  /* Code mirror specific styles */

  --jp-mirror-editor-keyword-color: #008000;
  --jp-mirror-editor-atom-color: #88f;
  --jp-mirror-editor-number-color: #080;
  --jp-mirror-editor-def-color: #00f;
  --jp-mirror-editor-variable-color: var(--md-grey-900);
  --jp-mirror-editor-variable-2-color: #05a;
  --jp-mirror-editor-variable-3-color: #085;
  --jp-mirror-editor-punctuation-color: #05a;
  --jp-mirror-editor-property-color: #05a;
  --jp-mirror-editor-operator-color: #aa22ff;
  --jp-mirror-editor-comment-color: #408080;
  --jp-mirror-editor-string-color: #ba2121;
  --jp-mirror-editor-string-2-color: #708;
  --jp-mirror-editor-meta-color: #aa22ff;
  --jp-mirror-editor-qualifier-color: #555;
  --jp-mirror-editor-builtin-color: #008000;
  --jp-mirror-editor-bracket-color: #997;
  --jp-mirror-editor-tag-color: #170;
  --jp-mirror-editor-attribute-color: #00c;
  --jp-mirror-editor-header-color: blue;
  --jp-mirror-editor-quote-color: #090;
  --jp-mirror-editor-link-color: #00c;
  --jp-mirror-editor-error-color: #f00;
  --jp-mirror-editor-hr-color: #999;

  /* Vega extension styles */

  --jp-vega-background: white;

  /* Sidebar-related styles */

  --jp-sidebar-min-width: 250px;

  /* Search-related styles */

  --jp-search-toggle-off-opacity: 0.5;
  --jp-search-toggle-hover-opacity: 0.8;
  --jp-search-toggle-on-opacity: 1;
  --jp-search-selected-match-background-color: rgb(245, 200, 0);
  --jp-search-selected-match-color: black;
  --jp-search-unselected-match-background-color: var(
    --jp-inverse-layout-color0
  );
  --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

  /* Icon colors that work well with light or dark backgrounds */
  --jp-icon-contrast-color0: var(--md-purple-600);
  --jp-icon-contrast-color1: var(--md-green-600);
  --jp-icon-contrast-color2: var(--md-pink-600);
  --jp-icon-contrast-color3: var(--md-blue-600);
}
</style>

<style type="text/css">
a.anchor-link {
   display: none;
}
.highlight  {
    margin: 0.4em;
}

/* Input area styling */
.jp-InputArea {
    overflow: hidden;
}

.jp-InputArea-editor {
    overflow: hidden;
}

@media print {
  body {
    margin: 0;
  }
}
</style>

<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-AMS_CHTML-full,Safe"> </script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    init_mathjax = function() {
        if (window.MathJax) {
        // MathJax loaded
            MathJax.Hub.Config({
                TeX: {
                    equationNumbers: {
                    autoNumber: "AMS",
                    useLabelIds: true
                    }
                },
                tex2jax: {
                    inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                    displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                    processEscapes: true,
                    processEnvironments: true
                },
                displayAlign: 'center',
                CommonHTML: {
                    linebreaks: { 
                    automatic: true 
                    }
                }
            });
        
            MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
        }
    }
    init_mathjax();
    </script>
    <!-- End of mathjax configuration --></head>
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
<div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[1]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[2]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">earthquakes</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;all_month.csv&#39;</span><span class="p">)</span>
<span class="n">earthquakes</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[2]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>time</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>depth</th>
      <th>mag</th>
      <th>magType</th>
      <th>nst</th>
      <th>gap</th>
      <th>dmin</th>
      <th>rms</th>
      <th>...</th>
      <th>updated</th>
      <th>place</th>
      <th>type</th>
      <th>horizontalError</th>
      <th>depthError</th>
      <th>magError</th>
      <th>magNst</th>
      <th>status</th>
      <th>locationSource</th>
      <th>magSource</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-11-30T12:18:16.030Z</td>
      <td>38.833000</td>
      <td>-122.805000</td>
      <td>1.97</td>
      <td>1.44</td>
      <td>md</td>
      <td>31.0</td>
      <td>50.0</td>
      <td>0.01038</td>
      <td>0.02</td>
      <td>...</td>
      <td>2021-11-30T12:21:30.201Z</td>
      <td>7km W of Cobb, CA</td>
      <td>earthquake</td>
      <td>0.17</td>
      <td>0.31</td>
      <td>0.13</td>
      <td>7.0</td>
      <td>automatic</td>
      <td>nc</td>
      <td>nc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021-11-30T12:17:42.360Z</td>
      <td>38.834835</td>
      <td>-122.805168</td>
      <td>1.98</td>
      <td>0.22</td>
      <td>md</td>
      <td>13.0</td>
      <td>61.0</td>
      <td>0.01205</td>
      <td>0.01</td>
      <td>...</td>
      <td>2021-11-30T12:19:17.907Z</td>
      <td>7km WNW of Cobb, CA</td>
      <td>earthquake</td>
      <td>0.32</td>
      <td>0.72</td>
      <td>0.14</td>
      <td>2.0</td>
      <td>automatic</td>
      <td>nc</td>
      <td>nc</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021-11-30T11:50:23.770Z</td>
      <td>19.332834</td>
      <td>-155.099503</td>
      <td>1.63</td>
      <td>1.87</td>
      <td>md</td>
      <td>30.0</td>
      <td>164.0</td>
      <td>NaN</td>
      <td>0.30</td>
      <td>...</td>
      <td>2021-11-30T11:53:40.990Z</td>
      <td>15 km SSE of Fern Forest, Hawaii</td>
      <td>earthquake</td>
      <td>0.63</td>
      <td>0.64</td>
      <td>0.94</td>
      <td>12.0</td>
      <td>automatic</td>
      <td>hv</td>
      <td>hv</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-11-30T11:37:13.280Z</td>
      <td>17.979500</td>
      <td>-67.004000</td>
      <td>10.00</td>
      <td>2.70</td>
      <td>md</td>
      <td>20.0</td>
      <td>155.0</td>
      <td>0.04150</td>
      <td>0.15</td>
      <td>...</td>
      <td>2021-11-30T11:52:24.629Z</td>
      <td>4 km E of La Parguera, Puerto Rico</td>
      <td>earthquake</td>
      <td>0.45</td>
      <td>0.59</td>
      <td>0.16</td>
      <td>10.0</td>
      <td>reviewed</td>
      <td>pr</td>
      <td>pr</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021-11-30T11:33:05.650Z</td>
      <td>38.835167</td>
      <td>-122.805168</td>
      <td>1.78</td>
      <td>0.85</td>
      <td>md</td>
      <td>10.0</td>
      <td>77.0</td>
      <td>0.01202</td>
      <td>0.01</td>
      <td>...</td>
      <td>2021-11-30T11:34:42.006Z</td>
      <td>7km WNW of Cobb, CA</td>
      <td>earthquake</td>
      <td>0.32</td>
      <td>1.04</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>automatic</td>
      <td>nc</td>
      <td>nc</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Notes: Using groupby on Type (Earthquake, Explosions, Ice quake, Quarry Blast?), groupby Location then place, Magnitudes bigger than or equal to 5. Questions: Which locations are hit by (event) most frequently? What time (window) do the events most often occur? What is relationship between time of day and an event occuring? Are there any predictors/strong relationships/indicators that an event is going to occur? Average magnitude per event compared?</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[3]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">earthquakes</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[3]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>latitude</th>
      <th>longitude</th>
      <th>depth</th>
      <th>mag</th>
      <th>nst</th>
      <th>gap</th>
      <th>dmin</th>
      <th>rms</th>
      <th>horizontalError</th>
      <th>depthError</th>
      <th>magError</th>
      <th>magNst</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9134.000000</td>
      <td>9134.000000</td>
      <td>9134.000000</td>
      <td>9133.000000</td>
      <td>6564.000000</td>
      <td>7580.000000</td>
      <td>6370.000000</td>
      <td>9133.000000</td>
      <td>6740.000000</td>
      <td>9133.000000</td>
      <td>6993.000000</td>
      <td>7577.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>36.529624</td>
      <td>-112.178530</td>
      <td>22.755205</td>
      <td>1.675445</td>
      <td>21.284126</td>
      <td>116.696895</td>
      <td>0.660005</td>
      <td>0.275026</td>
      <td>1.676261</td>
      <td>2.276648</td>
      <td>0.327450</td>
      <td>14.108618</td>
    </tr>
    <tr>
      <th>std</th>
      <td>19.612662</td>
      <td>63.009157</td>
      <td>53.944145</td>
      <td>1.221161</td>
      <td>15.674889</td>
      <td>58.743783</td>
      <td>2.292870</td>
      <td>0.288512</td>
      <td>3.008785</td>
      <td>9.457025</td>
      <td>0.601628</td>
      <td>26.664414</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-62.624300</td>
      <td>-179.967300</td>
      <td>-7.300000</td>
      <td>-1.210000</td>
      <td>0.000000</td>
      <td>12.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.080000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>33.318542</td>
      <td>-149.782175</td>
      <td>3.152500</td>
      <td>0.850000</td>
      <td>10.000000</td>
      <td>72.000000</td>
      <td>0.019095</td>
      <td>0.090000</td>
      <td>0.280000</td>
      <td>0.470000</td>
      <td>0.110000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>38.168950</td>
      <td>-121.142751</td>
      <td>8.305000</td>
      <td>1.480000</td>
      <td>16.000000</td>
      <td>103.000000</td>
      <td>0.063889</td>
      <td>0.150000</td>
      <td>0.490000</td>
      <td>0.780000</td>
      <td>0.170000</td>
      <td>8.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>44.980667</td>
      <td>-116.000975</td>
      <td>19.200000</td>
      <td>2.100000</td>
      <td>28.000000</td>
      <td>151.000000</td>
      <td>0.175900</td>
      <td>0.397600</td>
      <td>0.935134</td>
      <td>1.570000</td>
      <td>0.264000</td>
      <td>15.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>85.862200</td>
      <td>179.941000</td>
      <td>632.600000</td>
      <td>7.500000</td>
      <td>221.000000</td>
      <td>354.680000</td>
      <td>35.610000</td>
      <td>2.910000</td>
      <td>20.600000</td>
      <td>751.600000</td>
      <td>5.470000</td>
      <td>593.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[4]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">earthquakes</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[4]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>time                  0
latitude              0
longitude             0
depth                 0
mag                   1
magType               1
nst                2570
gap                1554
dmin               2764
rms                   1
net                   0
id                    0
updated               0
place                 0
type                  0
horizontalError    2394
depthError            1
magError           2141
magNst             1557
status                0
locationSource        0
magSource             0
dtype: int64</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[5]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fg</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">()</span>
<span class="n">earthquakes</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span><span class="n">column</span><span class="o">=</span><span class="s1">&#39;mag&#39;</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[5]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:&gt;</pre>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAWoAAAD4CAYAAADFAawfAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjQuMywgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/MnkTPAAAACXBIWXMAAAsTAAALEwEAmpwYAAANIUlEQVR4nO3df2zcdR3H8df72to6RJYFvD+Y2el+YJtSYnLRP9hI68T4c5oYDTXOsDUp09FARiLbGmOMqTozCCTVZD86IEiqov4hFlBDewljSmgFGawaCG5x/tgwMfxYsHTs7R/rZsfa9Xuu337fd/d8JAu9H717Lzme++Rz37uvubsAAHHlsh4AAHBhhBoAgiPUABAcoQaA4Ag1AARXn8aDXn755V4oFNJ4aOCinDhxQpdccknWYwDnGRsb+5e7XzHTbamEulAoaHR0NI2HBi5KqVRSe3t71mMA5zGzI7PdxtYHAARHqAEgOEINAMERagAIjlADQHCEGjVhcHBQra2tWrt2rVpbWzU4OJj1SEBiqRyeB0QyODio3t5eDQwM6K233lJdXZ26urokSZ2dnRlPB8yNFTWqXl9fnwYGBtTR0aH6+np1dHRoYGBAfX19WY8GJEKoUfXGx8e1evXqc65bvXq1xsfHM5oIKA+hRtVrbm7W/v37z7lu//79am5uzmgioDyEGlWvt7dXXV1dGhkZ0cmTJzUyMqKuri719vZmPRqQCG8mouqdecOwp6dH4+Pjam5uVl9fH28komJYGudMLBaLzpcyISK+lAlRmdmYuxdnuo2tDwAIjlADQHCEGgCCI9QAEByhBoDgCDUABEeoASA4Qg0AwRFqAAiOUANAcIQaAIIj1AAQHKEGgOAINWoCJ7dFJeP7qFH1OLktKh0ralQ9Tm6LSkeoUfU4uS0qHaFG1ePktqh0hBpVj5PbotLxZiKqXmdnp+69916tXbtW7i4z0/XXX88biagYrKhR9Xp6ejQ8PKydO3fqkUce0c6dOzU8PKyenp6sRwMSIdSoenv27NGOHTu0ZcsWNTU1acuWLdqxY4f27NmT9WhAIoQaVW9iYkJDQ0PK5XLq6OhQLpfT0NCQJiYmsh4NSIRQo+qZmYaHh7Vp0yY99NBD2rRpk4aHh2VmWY8GJEKoUfXOvIG4YsUK1dfXa8WKFTIzuXvWowGJcNQHakJXV5e2b9+uiYkJNTY2qqurS3v37s16LCARS7KqMLPFkvZKapXkkja6++9mu3+xWPTR0dH5mhG4KLlcTmamU6dOnXOdu59zHZAlMxtz9+JMtyXd+rhb0qPu/gFJ10jis7eoKKdOnVJTU5P6+/vV1NREoFFR5tz6MLN3S7pO0o2S5O5vSnoz3bGA+ePuamho0MTEhG6++WaZmRoaGjQ5OZn1aEAiSfao3y/pZUn3mNk1ksYk3eLuJ6bfycy6JXVLUj6fV6lUmudRgf/fmjVr9Pjjj2tyclL19fVas2aNhoeHeZ2iIsy5R21mRUm/l3Stuz9pZndLetXdvzHb77BHjUjOHIZ3xx13qKWlRYcOHdJtt90mSRz5gTAutEedZEV9VNJRd39y6vLPJG2dr+GAhXImzkClmfPNRHf/p6S/mtlVU1etlXQo1akAAGclPY66R9IDZvYOSS9J2pDeSMD8e/ubh7yZiEqS6PA8d3/G3Yvu3ubun3P3f6c9GDCfJicnVSgUdP/996tQKBBpVBQ+mYiacfjwYa1fvz7rMYCy8V0fqBn5fF733HOP8vl81qMAZWFFjZqQy+V0/PhxbdiwQWamXC7HpxNRMQg1asL0KLs7x0+jorD1AQDBEWoACI5QA0BwhBoAgiPUqCm33npr1iMAZSPUqCl33XVX1iMAZSPUqCmsqFGJCDVqCitqVCJCDQDBEWoACI5QA0BwhBoAgiPUABAcoUZNWbp0adYjAGUj1KgpR48ezXoEoGyEGgCCI9QAEByhBoDgCDUABEeoASA4Qg0AwRFqAAiOUANAcIQaAIIj1AAQHKEGgOAINQAER6gBIDhCDQDBEWoACI5QA0BwhBoAgiPUABBc4lCbWZ2ZPW1mv0pzIADAucpZUd8iaTytQQAAM0sUajNbKulTkvamOw6QrpUrV2Y9AlC2+oT3u0vS1yVdOtsdzKxbUrck5fN5lUqli50NuKCOjo6yf+eFF14457KZJfq9kZGRsp8LmC9zhtrMPi3puLuPmVn7bPdz992SdktSsVj09vZZ7wrMC3dPdL8zMc7n8zp27Ljy+ffo2LFjZT0GkKUkWx/XSlpnZocl/VjSR8zsR6lOBaTgdJz9bKSBSjFnqN19m7svdfeCpBskDbv7l1OfDJgns62aWU2jUnAcNWqCu8vdtez2X539GagUSd9MlCS5e0lSKZVJAAAzYkUNAMERagAIjlADQHCEGgCCI9QAEByhBoDgCDUABEeoASA4Qg0AwRFqAAiOUANAcIQaAIIj1AAQHKEGgOAINQAER6gBIDhCDQDBEWoACI5QA0BwhBoAgiPUABAcoQaA4Ag1AARHqAEgOEINAMERagAIjlADQHCEGgCCI9QAEByhBoDgCDUABEeoASA4Qg0AwRFqAAiOUANAcIQaAIKbM9Rm9l4zGzGzcTN73sxuWYjBAACn1Se4z0lJt7n7H8zsUkljZvZbdz+U8myoMdd86zd65Y3J1J+nsHUo1ce/7J0N+uM3P5bqc6C2zBlqd/+HpH9M/fyamY1LulISoca8euWNSR3+3qdSfY5SqaT29vZUnyPtfwhQe5KsqM8ys4KkD0p6cobbuiV1S1I+n1epVJqH8VBr0n7dvP766wvy2uT1j/mUONRm9i5JP5d0q7u/+vbb3X23pN2SVCwWPe1VC6rQo0Opr3YXYkW9EH8P1JZER32YWYNOR/oBd/9FuiMBAKZLctSHSRqQNO7ud6Y/EgBguiQr6mslrZf0ETN7ZurPJ1OeCwAwJclRH/sl2QLMAgCYAZ9MBIDgCDUABEeoASA4Qg0AwRFqAAiOUANAcGV91weQpkubt+rq+7am/0T3pfvwlzZLUrpfLoXaQqgRxmvj3+Pb84AZsPUBAMERagAIjlADQHCEGgCCI9QAEByhBoDgCDUABEeoASA4Qg0AwRFqAAiOUANAcIQaAILjS5kQyoJ8odGj6T7HZe9sSPXxUXsINcJI+5vzpNP/ECzE8wDzia0PAAiOUANAcIQaAIIj1AAQHKEGgOAINQAER6gBIDhCDQDBEWoACI5QA0BwhBoAgiPUABAcoQaA4Ag1AASXKNRm9nEz+7OZvWhmW9MeCgDwP3OG2szqJP1A0icktUjqNLOWtAcDAJyWZEX9IUkvuvtL7v6mpB9L+my6YwEAzkhyhpcrJf112uWjkj789juZWbekbknK5/MqlUrzMR8w73htotIkCbXNcJ2fd4X7bkm7JalYLHp7e/vFTQak4dEh8dpEpUmy9XFU0nunXV4q6e/pjAMAeLskoX5K0koze5+ZvUPSDZJ+me5YAIAz5tz6cPeTZnazpF9LqpO0z92fT30yAICkZHvUcveHJT2c8iwAgBnwyUQACI5QA0BwhBoAgiPUABAcoQaA4Ag1AARHqAEgOEINAMERagAIjlADQHCEGgCCI9QAEByhBoDgCDUABEeoASA4Qo2a0NbWJjPTkR2flpmpra0t65GAxAg1ql5bW5sOHjyodevW6crNP9K6det08OBBYo2KYe7nnVD8ohWLRR8dHZ33xwWmM7MFe640/j8BpjOzMXcvznQbK2pULHdP9EeSNm7cqMbGRklSY2OjNm7cWPZjAFkh1KgJ+/bt0+LFiyVJixcv1r59+7IdCCgDoUbNWL58uR588EEtX74861GAsiQ6CzlQ6ZYtW6YDBw7owIEDZy8fOXIk46mAZFhRoyZs3rxZ7q6RkRG5uzZv3pz1SEBirKhR9ZYsWaJt27aprq5OLS0tuvPOO7Vt2zYtWbIk69GARAg1ql5/f79uuukmbd26VZOTk2poaNCiRYvU39+f9WhAImx9oOp1dnZq165dWrVqlXK5nFatWqVdu3aps7Mz69GARPjAC2pKqVRSe3t71mMA5+EDLwBQwQg1AARHqAEgOEINAMERagAILpWjPszsZUl8PhcRXS7pX1kPAcxgmbtfMdMNqYQaiMrMRmc7BAqIiq0PAAiOUANAcIQatWZ31gMA5WKPGgCCY0UNAMERagAIjlADQHCEGgCCI9SoCmZWMLM/mdleM3vOzB4ws4+a2RNm9oKZfWjqzwEze3rqv1dN/e4iM/upmT1rZj8xsyfNjA/FIAxOxYVqskLSFyR1S3pK0pckrZa0TtJ2SV+RdJ27nzSzj0r6jqTPS/qapH+7e5uZtUp6JoPZgVkRalSTv7j7QUkys+clPebubmYHJRUkXSbpPjNbKcklNUz93mpJd0uSuz9nZs8u+OTABbD1gWoyMe3nU9Mun9LpRcm3JY24e6ukz0hqmrrdFmxC4P9AqFFLLpP0t6mfb5x2/X5JX5QkM2uRdPXCjgVcGKFGLfm+pO+a2ROS6qZd/0NJV0xtedwu6VlJr2QwHzAjPkKOmmdmdZIa3P0/ZrZc0mOSVrn7mxmPBkjizURAkhZJGjGzBp3er/4qkUYkrKgBIDj2qAEgOEINAMERagAIjlADQHCEGgCC+y9vJXjYwhPa4AAAAABJRU5ErkJggg=="
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[6]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">earthquakes</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;type&#39;</span><span class="p">])</span><span class="o">.</span><span class="n">count</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[6]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>time</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>depth</th>
      <th>mag</th>
      <th>magType</th>
      <th>nst</th>
      <th>gap</th>
      <th>dmin</th>
      <th>rms</th>
      <th>...</th>
      <th>id</th>
      <th>updated</th>
      <th>place</th>
      <th>horizontalError</th>
      <th>depthError</th>
      <th>magError</th>
      <th>magNst</th>
      <th>status</th>
      <th>locationSource</th>
      <th>magSource</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>chemical explosion</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>earthquake</th>
      <td>8947</td>
      <td>8947</td>
      <td>8947</td>
      <td>8947</td>
      <td>8946</td>
      <td>8946</td>
      <td>6411</td>
      <td>7428</td>
      <td>6217</td>
      <td>8947</td>
      <td>...</td>
      <td>8947</td>
      <td>8947</td>
      <td>8947</td>
      <td>6608</td>
      <td>8947</td>
      <td>6842</td>
      <td>7424</td>
      <td>8947</td>
      <td>8947</td>
      <td>8947</td>
    </tr>
    <tr>
      <th>explosion</th>
      <td>49</td>
      <td>49</td>
      <td>49</td>
      <td>49</td>
      <td>49</td>
      <td>49</td>
      <td>41</td>
      <td>41</td>
      <td>41</td>
      <td>49</td>
      <td>...</td>
      <td>49</td>
      <td>49</td>
      <td>49</td>
      <td>41</td>
      <td>49</td>
      <td>41</td>
      <td>41</td>
      <td>49</td>
      <td>49</td>
      <td>49</td>
    </tr>
    <tr>
      <th>ice quake</th>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>26</td>
      <td>...</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>0</td>
      <td>26</td>
      <td>0</td>
      <td>0</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
    </tr>
    <tr>
      <th>other event</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>quarry blast</th>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>...</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>89</td>
      <td>109</td>
      <td>108</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
      <td>109</td>
    </tr>
    <tr>
      <th>sonic boom</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>7 rows × 21 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[7]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">earthquakes</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;type&#39;</span><span class="p">])</span><span class="o">.</span><span class="n">sum</span><span class="p">()[</span><span class="s1">&#39;mag&#39;</span><span class="p">]</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[7]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>type
chemical explosion        1.770000
earthquake            15035.670002
explosion                74.070000
ice quake                37.300000
other event               1.560000
quarry blast            151.470000
sonic boom                0.000000
Name: mag, dtype: float64</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[8]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">earthquakes</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;type&#39;</span><span class="p">])</span><span class="o">.</span><span class="n">count</span><span class="p">()[</span><span class="s1">&#39;mag&#39;</span><span class="p">]</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[8]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>type
chemical explosion       1
earthquake            8946
explosion               49
ice quake               26
other event              1
quarry blast           109
sonic boom               1
Name: mag, dtype: int64</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[9]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">averageMag</span> <span class="o">=</span> <span class="n">earthquakes</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;type&#39;</span><span class="p">])</span><span class="o">.</span><span class="n">sum</span><span class="p">()[</span><span class="s1">&#39;mag&#39;</span><span class="p">]</span><span class="o">/</span><span class="n">earthquakes</span><span class="o">.</span><span class="n">groupby</span><span class="p">([</span><span class="s1">&#39;type&#39;</span><span class="p">])</span><span class="o">.</span><span class="n">count</span><span class="p">()[</span><span class="s1">&#39;mag&#39;</span><span class="p">]</span>
<span class="n">averageMag</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[9]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>type
chemical explosion    1.770000
earthquake            1.680714
explosion             1.511633
ice quake             1.434615
other event           1.560000
quarry blast          1.389633
sonic boom            0.000000
Name: mag, dtype: float64</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[10]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">averageMag</span> <span class="o">=</span> <span class="n">averageMag</span><span class="o">.</span><span class="n">to_frame</span><span class="p">(</span><span class="s1">&#39;Average Magnitude&#39;</span><span class="p">)</span>
<span class="n">averageMag</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">averageMag</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[10]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>Average Magnitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>chemical explosion</td>
      <td>1.770000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>earthquake</td>
      <td>1.680714</td>
    </tr>
    <tr>
      <th>2</th>
      <td>explosion</td>
      <td>1.511633</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ice quake</td>
      <td>1.434615</td>
    </tr>
    <tr>
      <th>4</th>
      <td>other event</td>
      <td>1.560000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>quarry blast</td>
      <td>1.389633</td>
    </tr>
    <tr>
      <th>6</th>
      <td>sonic boom</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[11]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig1</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">()</span>
<span class="n">averageMag</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">kind</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">x</span><span class="o">=</span><span class="s1">&#39;type&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;Average Magnitude&#39;</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">ax</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;orange&#39;</span><span class="p">,</span><span class="s1">&#39;brown&#39;</span><span class="p">,</span><span class="s1">&#39;red&#39;</span><span class="p">,</span><span class="s1">&#39;blue&#39;</span><span class="p">,</span><span class="s1">&#39;green&#39;</span><span class="p">,</span><span class="s1">&#39;gray&#39;</span><span class="p">],</span> <span class="n">title</span><span class="o">=</span><span class="s1">&#39;Average Magnitude Per Event&#39;</span><span class="p">,</span> <span class="n">ylabel</span><span class="o">=</span><span class="s1">&#39;Average Magnitude&#39;</span><span class="p">,</span> <span class="n">xlabel</span><span class="o">=</span><span class="s1">&#39;Event Type&#39;</span><span class="p">,</span> <span class="n">legend</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">tight_layout</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[12]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig1</span><span class="o">.</span><span class="n">savefig</span><span class="p">(</span><span class="s1">&#39;Figure1_AvMag.jpg&#39;</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[13]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Magnitude</span> <span class="o">=</span> <span class="n">earthquakes</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,[</span><span class="s1">&#39;mag&#39;</span><span class="p">]]</span>
<span class="n">Magnitude</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[13]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mag</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.44</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.87</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2.70</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.85</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>9129</th>
      <td>0.34</td>
    </tr>
    <tr>
      <th>9130</th>
      <td>0.65</td>
    </tr>
    <tr>
      <th>9131</th>
      <td>2.29</td>
    </tr>
    <tr>
      <th>9132</th>
      <td>4.90</td>
    </tr>
    <tr>
      <th>9133</th>
      <td>-0.01</td>
    </tr>
  </tbody>
</table>
<p>9134 rows × 1 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mag_list</span> <span class="o">=</span> <span class="n">Magnitude</span><span class="o">.</span><span class="n">values</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">sum</span><span class="p">(</span><span class="n">mag_list</span><span class="p">,</span> <span class="p">[]))</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[16]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Mag</span> <span class="o">=</span> <span class="p">(</span><span class="nb">sum</span><span class="p">(</span><span class="n">mag_list</span><span class="p">,</span> <span class="p">[]))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">Mag</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>[1.44, 0.22, 1.87, 2.7, 0.85, 1.29, 4.3, 0.37, 5.0, 0.36, 4.9, 5.0, 1.3, 0.82, 5.0, 1.8, 6.0, 0.4, 2.78, 1.1, 1.69, 1.3, 0.83, 2.1, 0.8, 0.36, 2.08, 2.1, 2.18, 0.9, 1.92, 1.01, 2.1, 2.86, 1.7, 1.26, 1.9, 1.4, 0.29, 1.0, 2.4000001, 2.4, 2.2, 2.17, 1.19, 1.0, 1.0, 2.1, 2.57, 0.61, 5.5, 0.7, 0.81, 1.54, 0.69, 4.5, 1.4, 2.27999997, 0.98, 0.48, 0.49, 0.73, 0.37, 0.37, 0.3, 0.86, 0.82, 1.3, 1.94, 1.11, 0.98, 0.93, 5.0, 0.6, 0.87, 1.78, 0.88, 2.7, 4.9, 1.46, 0.86, 2.08, 2.27999997, 0.36, 2.51, 2.1, 0.66, 3.16, 0.87, 0.86, 0.84, 0.23, 1.95000005, 0.35, 0.86, 1.5, 1.86000001, 0.75, 0.73, 4.6, 0.6, 2.76, 2.57, 0.4, 0.86, 0.49, 1.53, 4.3, 2.49, 5.1, 1.55, 1.63, 4.6, 0.36, 2.51, 1.86000001, 1.3, 2.84, 1.91, 4.4, 0.98, 0.68, 1.3, 2.57, 1.90999997, 0.37, 1.6, 2.08999991, 4.7, 0.36, 1.57, 1.79, 4.6, 0.9, 0.76, 0.18, 2.4, 2.00999999, 1.8, 4.4, 1.5, 1.13, 0.7, 0.53, 2.21, 1.7, 0.21, 2.85, 0.21, 0.33, 4.9, 1.88999999, 4.6, 4.6, 2.0, 2.41, 1.21, 4.7, 0.46, 2.1, 1.23, 1.8, 1.85, 2.0999999, 0.85, 2.9, 1.83000004, 5.4, 0.97, 1.1, 1.0, 2.1500001, 1.6, 1.25, 1.7, 2.5, 1.5, 2.21, 3.06, 1.18, 0.8, 1.42, 1.88, 4.6, 2.5, 1.3, 0.38, 0.71, 0.85, 1.71000004, 0.9, 0.92, 1.0, 1.62, 4.6, 1.4, 3.7, 1.39, 2.0, 1.18, 0.61, 1.92, 2.64, 2.08, 1.78, 2.21, 4.7, 2.1, 2.3, 1.1, 2.19, 0.89, 2.5, 1.9, 0.18, 0.17, 0.36, 1.3, 6.3, -0.48, 1.1, 1.12, 1.23, 3.22, 1.85000002, 1.8, 2.0, 1.03, 1.34, 0.87, 1.7, 4.0, 1.3, 0.96, 0.9, 0.2, 1.45, 2.33, 1.6, 0.92, 1.6, 0.36, 0.43, 0.66, 0.95, 0.92, 1.86000001, 0.78, 1.3, 1.6, 1.6, 1.4, 0.6, 2.31, 1.6, 5.1, 2.61, 4.2, 2.4, 1.5, 0.86, 1.70000005, 1.39, 1.89, 0.86, 3.6, 4.4, 1.43, 0.9, 2.25, 1.55, 0.49, 1.6, 1.4, 0.38, 0.73, 2.1400001, 2.0, 1.03, 3.51, 0.94, 2.2, 4.3, 2.18, 4.5, 1.25, 2.0, 1.04, 4.3, 0.9, 1.5, 1.03, 1.0, 2.47, 1.1, 1.1, 1.0, 0.98, 1.55, 1.4, 1.88, 1.5, 1.93, 0.85, 1.4, 1.6, 1.1, 2.69, 2.1, 0.42, 2.34, 0.55, 0.62, 2.31999993, 2.03, 0.97, 2.1, 1.83000004, 1.83000004, 1.97, 0.85, 4.2, 4.1, 1.91, 4.3, 2.61, 2.44, 2.3, 1.58, 1.3, 1.03, 2.25, -0.26, 0.89, 2.4, 0.6, 2.05999994, 2.5, 0.98, 1.45, 1.1, 1.6, 1.8, 0.74, 1.16, 2.3, 1.7, 1.35, 1.3, -0.63, 1.2, 2.37, 1.6, 1.58, 1.71, 1.7, 1.2, 1.7, 2.41, 1.7, 1.0, 1.0, 1.3, 1.3, 0.46, 1.44, 2.27, 3.3, 1.42, 2.7, 0.54, 3.1, 0.4, 4.3, 0.41, 1.1, 4.6, 1.91999996, 1.0, 4.1, -1.0, 0.56, 0.46, 2.21000004, 2.44, 1.2, 2.32, -0.04, 1.12, 1.7, 1.7, 0.35, 0.59, 1.89, -0.59, 4.6, 4.7, 2.89, 2.5, 1.02, 1.73, 2.6, 1.11, 1.46, 0.86, 1.64, 1.71, 0.86, 1.93, 2.5, 0.36, 0.47, 3.12, 1.8, 2.20000005, 2.0, 3.1, 1.19, 0.6, 2.32, 2.38, 0.7, 4.5, 1.17, 1.31, 1.9, 4.5, 1.80999994, 0.8, 4.3, 1.87, 1.88, 1.2, 1.7, 1.24, 3.28, 0.8, 1.0, 2.97, 3.6, 4.2, 0.8, 0.5, 3.56, 1.19, 0.7, 0.67, 1.0, 1.5, 1.27, 0.8, 0.9, 2.77, 1.59, 4.5, 1.7, -0.47, 2.00999999, 1.7, 0.28, 1.74000001, 4.9, 1.7, 2.1, 1.68, 2.9, 0.59, 1.17, 0.57, 0.93, 1.9, 2.2, 0.21, 1.19, 0.36, 1.97, 2.2, 1.7, 1.92999995, 1.01, 2.33, 1.87, 1.2, 1.13, 0.58, 0.4, 1.75999999, 1.9, 1.51, 0.61, 3.07, 1.75999999, 2.03999996, 0.86, 2.71, 7.5, 1.58, 0.54, 1.04, 1.35, 0.6, 0.99, 1.0, 0.9, 1.4, 0.17, 1.78999996, 0.44, 0.58, 1.9, 1.8, 1.42, 1.9, 0.5, 4.5, 0.36, 0.84, 0.67, 1.8, 4.0, 0.62, -0.05, 0.78, 0.84, 0.88, 2.08, 1.48, 0.19, 2.24000001, 1.57, 4.2, 1.69, 2.9, 2.71, 2.44, -0.48, 2.30999994, 1.35, 0.7, 0.49, 2.63, 0.68, 2.2, 2.7, 1.4, 0.37, 2.04999995, 2.9, 1.99, 2.74, 0.75, 2.38, 1.4, 1.0, 0.85, 0.9, 4.1, 0.73, 1.7, 3.0, 5.1, 2.9, 1.1, 2.29, 3.2, 1.14, 0.6, 1.25, 0.72, 2.8, 3.2, 1.27, 0.58, 0.73, 1.87, 2.04999995, 1.56, 1.37, 2.25999999, 1.61, 2.4000001, 1.33, 1.32, 0.37, 1.22, 1.63, 1.7, 0.9, 1.2, 0.85, 1.9, 0.67, 0.85, 2.0, 0.41, 3.0, 1.06, 1.41, 3.25, 0.95, 1.6, 0.63, 3.46, 1.34, 4.4, 3.33, 1.34, 2.11, 1.5, 1.2, 2.26, 1.7, 0.99, 2.3, 0.86, 0.79, 0.95, 3.04, 1.2, 2.8, 0.58, 4.3, 3.7, 1.15, 4.7, 1.4, 4.6, 2.79, 2.3, 1.6, 1.7, 0.8, 1.44, -1.0, 2.74, 1.44, 0.84, 4.1, 0.6, 1.15, 0.73, 1.99, 1.85000002, 1.91999996, 1.88999999, 2.0, 0.82, 1.76999998, 0.9, 3.0, 0.96, 0.32, 1.37, 1.5, -0.92, 1.2, 1.4, 2.54, 1.1, 0.8, 1.2, 0.91, 4.6, 1.6, 1.4, 1.5, 4.9, 4.8, 2.41, 0.36, 0.55, 0.89, -0.78, 0.6, 2.1, 1.7, 1.21, 0.35, 1.31, 0.28, 0.9, 1.24, 2.65, 1.4, 0.47, 1.84000003, 1.2, 1.35, 4.1, 2.4, 5.3, 1.3, 0.59, 1.74, 0.66, 1.78, 0.21, 1.86000001, 0.87, 4.3, 0.86, 4.4, -0.21, 4.6, 1.5, 1.8, 2.2, 2.24000001, 1.6, 0.32, 0.54, 1.99, 5.3, 4.6, 0.74, 1.7, 2.02, 1.7, 1.1, 0.05, 4.6, 0.85, 1.1, 1.88999999, 2.44, 0.7, 2.3, 1.06, 0.8, 3.0, 0.83, 1.08, 2.1, 1.4, 3.02, 3.27, 1.5, 1.84, 0.75, 0.72, 0.18, 1.76, 1.85000002, 0.6, 0.43, 0.47, 0.75, 0.84, 1.8, 2.93, 2.4, 1.8, 1.0, 0.98, 0.81, 3.2, 0.96, 0.65, 1.07, 1.6, 1.82, 1.16, 0.89, 0.93, 1.19, 1.59, 0.86, 1.4, 1.85, 0.85, 1.89, 0.56, 2.01999998, 0.74, 2.57, 0.77, 1.77, 1.04, 1.32, 1.6, 2.3, 1.25, 3.48, 0.4, 2.46, 0.8, -0.23, 0.61, 1.04, 2.8, 1.88, 2.01, 2.1, 1.0, 1.9, 1.88, 0.26, 0.66, 0.56, 0.41, 0.64, 1.7, 0.78, 0.3, 0.18, 0.74, 0.9, 1.6, 0.63, -0.23, -0.38, 2.16, 3.29, 0.9, 1.73, 1.94, 2.76, 3.46, 1.7, 1.8, 1.57, 0.8, 2.6, 0.87, 1.5, 4.9, 0.85, 2.12, 1.85000002, 2.17000008, 1.2, 0.74, 2.16000009, 1.90999997, 0.85, 0.67, 1.91, 2.1500001, 1.74, 0.63, 1.90999997, 0.9, 1.9, 2.0, 2.00999999, 2.15, 1.2, 0.9, 1.19, 0.96, 1.9, 1.8, 0.47, 2.61, 1.4, 2.77, 1.9, 1.57, 0.91, 1.2, 4.05, 1.02, 0.7, 1.99, 0.19, 0.44, 0.37, 1.71, 1.04, 1.22, 0.95, 1.2, 1.6, 1.11, 2.6, 1.5, 5.2, 1.90999997, 0.36, 1.8, 0.3, 0.85, 0.88, 0.68, 4.7, 2.53, 1.89, 0.93, 1.0, 4.4, 2.76, 0.93, 0.36, 1.19, 1.1, 0.86, 1.77, 2.1, 2.08, 0.85, 0.6, 0.58, -0.91, 4.5, 0.7, 2.13, 2.34, 2.32, 1.39, 1.2, 0.88, 2.17, 1.3, 5.4, 3.0, 1.69, 0.35, 2.0, 1.6, 0.08, 1.96, 2.9, 1.9, 0.8, 2.0, 4.0, 0.84, 0.47, 1.6, 0.7, 0.38, 1.3, 0.87, 1.61, 4.2, 0.88, 0.9, 5.3, 0.7, 1.88999999, 1.87, 1.52, -0.89, -0.54, 1.6, 1.8, 1.19, 0.3, 0.82, 0.55, 1.43, 2.35, 2.6, 0.99, 1.41, 1.13, 0.33, 1.2, 1.58, 0.6, 1.5, 1.84, 1.1, 0.61, 1.62, 1.6, 2.15, 0.45, 0.2, 1.8, 0.9, 2.82, 1.1, 2.92, 0.0, 1.2, 2.08, 3.2, 0.7, 0.85, 1.9, 2.09, 1.48, 2.08, 1.2, 1.74, 1.9, 1.84000003, 1.94000006, 1.77999997, 2.18, 3.56, -0.04, 2.6, 0.42, 2.1400001, 1.1, 5.1, 0.97, 2.75, 1.85000002, 2.3, 2.03, 2.45000005, 1.74, 0.84, 2.82, 2.18000007, 1.12, 2.1, 0.9, 0.78, 4.7, 1.51, 1.79999995, 1.82, 1.87, 0.76, 1.2, 1.6, 0.87, 1.68, 5.3, 5.3, 0.91, 0.93, 2.77, 1.8, 1.15, 1.39, 2.28999996, 1.1, 1.86, 2.0, 2.67, 1.4, 2.23, 0.61, 1.47, 1.26, 2.1, 0.73, 0.95, 0.85, 2.18, 1.18, 2.0999999, 3.7, 2.37, 0.42, 4.7, 1.66, 4.0, 0.36, 1.29, 1.15, 0.9, 1.93, 0.84, 1.88, 0.96, 0.91, 1.99, 4.4, 1.94, 0.36, 1.11, 1.15, 1.34, 0.94, 0.47, 0.04, 1.3, 0.89, 1.19, 1.39, 0.46, 0.5, 0.37, 2.08999991, 1.55, 1.88, 0.84, 4.3, 2.73, 2.8, 1.16, 0.38, 0.58, 3.4, 2.13000011, 1.2, 2.85, 2.2, 1.8, 1.5, 1.85000002, 0.9, 1.3, 0.55, 4.3, 1.17, 2.6, 1.7, 0.29, 2.5, 1.2, 1.0, 2.78, 2.42, 0.85, 1.3, 0.7, 0.65, 1.1, 0.4, 1.8, 0.7, 2.0, 0.6, 2.23, 1.0, 1.3, 0.68, -0.46, 3.17, 2.25999999, 0.89, 3.16, 2.31, 2.53, 0.19, 2.1400001, 1.37, 1.28, 1.51, 1.64, 0.8, 2.0, 0.36, 0.31, 0.4, 1.0, 3.36, 0.33, 1.17, 0.85, 4.4, 2.53, 1.69, 0.53, 5.7, 1.5, 1.2, 0.64, 0.52, 0.2, 1.9, 0.23, 2.03, 0.76, 0.12, 2.26999998, 1.6, 0.88, 1.7, 0.8, 1.8, 2.03999996, 2.35, 0.5, 1.7, 2.96, 0.5, 2.29, 0.67, 0.36, 1.4, 0.56, 5.8, 1.0, 1.1, 1.71, 2.04, 1.29, 2.41, 0.72, 2.21000004, 4.4, 1.98000002, 2.92, 3.96, 1.2, 0.29, 1.0, 2.1, 2.8, 0.7, 1.6, 1.15, 1.8, 1.89999998, 2.13, 1.64, 1.9, 1.7, 3.5, 0.85, 0.4, 1.2, 0.93, 1.24, 1.26, 1.83000004, 0.92, 1.25, 0.36, 1.88, 1.8, 0.82, 2.02999997, 1.5, 0.6, 1.49, 1.8, 0.8, 6.2, 1.86, 2.32, 1.0, 0.85, 0.45, 0.45, 1.6, 2.31, 0.35, 1.31, 4.5, 2.0, 0.54, 0.85, 1.41, 2.32, 0.74, 2.85, 0.11, 4.4, 0.46, 2.57, 1.19, 0.35, 0.21, 1.09, 0.47, 0.37, 4.4, 1.5, 4.6, 0.49, 1.8, 0.6, 2.0, 1.95, 1.19, 0.3, 1.18, 0.37, 1.99, 4.3, 1.6, 1.5, 3.36, 0.68, 1.0, 0.55, 1.9, 1.17, 1.3, 1.57, 1.96000004, 1.6, 3.34, 0.9, 1.6, 1.0, -0.01, 0.65, 1.85, 3.2, -1.03, 0.34, 2.53, 1.35, 1.7, 2.25999999, 1.44, 0.65, 2.3, 1.75, 1.6, 1.6, 0.89, 0.3, 1.7, 1.63, 4.4, 1.94, 1.3, 4.4, 3.49, 1.38, 1.75, 1.53, 0.72, 0.9, 0.92, 4.7, 1.41, 0.4, 1.0, 0.34, 1.0, 1.8, 2.09, 0.5, 0.3, 1.49, 0.8, 1.78999996, 0.8, 0.6, 1.0, 0.8, 2.0, 1.9, 0.41, 4.9, 0.72, 0.37, 6.0, 0.74, 2.25, 2.48000002, 2.09, 1.62, 1.8, 1.75, 0.36, 0.49, 2.0, 0.91, 0.67, 1.27, 2.72, 1.44, 1.6, 0.46, 3.12, 0.6, 2.68, 0.8, 2.1, 1.92999995, 1.2, 0.88, 1.6, 1.03, 1.29, 2.31, 1.6, 1.8, 1.16, 0.7, 2.05, 2.68, 0.76, 2.13, 1.6, -0.04, 1.93, 1.6, 0.9, 1.8, 1.03, 2.2, 1.6, 4.3, 1.4, 2.0, 2.05, 0.2, 1.9, 1.6, 1.76, 0.8, 1.08, 0.4, 2.01, 1.22, 1.2, 2.0, 2.88, 1.5, 2.0, 2.61, 3.7, 0.8, 0.51, 0.8, 2.09, 1.9, 4.7, 1.23, 5.0, 4.0, 1.7, 1.84, 4.1, 2.24, 1.5, 0.49, 1.82, 2.58, 0.85, 1.2, 2.09, 0.58, 0.37, 0.97, 2.11, 2.19, 1.72, 1.2, 1.38, 2.67, 1.42, 2.8, 0.84, 1.83, 1.7, 1.73, 4.5, 1.4, 4.6, 1.6, 1.4, 1.2, 0.85, -1.05, 1.5, 1.56, 2.15, 1.18, 1.5, 0.85, 0.85, 0.85, 0.36, 1.6, 1.1, 1.0, 0.36, 0.26, 2.6, 4.6, 4.9, 2.47, 0.87, 1.4, 0.05, 1.38, 1.68, 1.7, 2.6, 0.89, 1.18, 1.28, 1.19, 4.3, 0.36, 1.49, 4.2, 1.56, 1.9, 2.32, 0.55, 2.05999994, 1.7, 1.99000001, 0.87, 0.75, 1.08, 1.28, 3.8, 3.3, 1.89, 1.01, 1.21, 0.3, 1.3, 1.01, 4.6, 2.23, 1.15, 2.14, 2.17000008, 1.33, 2.21000004, 2.7, 1.82, 1.58, 0.84, 4.7, 4.6, 1.2, 2.11, 1.5, 0.5, 3.06, 1.0, 2.34, 1.3, 2.0, 3.44, 0.85, 0.23, 1.76, 0.98, 2.1, 1.31, 4.0, 1.01, 1.31, 2.57, 2.19, 1.87, 2.1, 1.25, 1.24, 1.61, 2.93, 2.3, 1.9, 1.94000006, 1.6, 4.4, 0.5, 1.53, 2.45, 2.14, 2.05, 1.26, 1.95, 1.59, 4.8, 0.9, 1.46, 1.94, 2.0, 1.03, 4.9, 1.3, 0.68, 1.5, 0.3, 1.98000002, 0.15, 2.6, 2.22, 2.19, 0.36, 0.5, 2.1, 1.1, 3.0, 1.86, 1.4, 0.04, 1.02, 2.34, 1.69, 1.63, 1.22, 1.2, 1.25, 1.77, 2.04, 1.6, 1.86, 0.12, 4.1, 1.5, 4.4, 1.65, 2.68, 1.7, 1.05, 2.2, 5.2, 1.37, 0.56, 4.6, 4.3, 1.37, 1.74000001, 2.51, 5.0, 1.99, 1.7, 1.92999995, 1.3, 2.33, 1.3, 1.69, 1.31, 2.06999993, 1.01, 2.06, 0.5, 0.22, 1.6, 4.9, 1.3, 1.43, 0.26, 0.26, 0.85, 0.58, 1.34, 2.2, 2.0, 2.05, 0.8, 1.6, 0.8, 0.85, 2.61, 0.5, 1.6, 1.6, 3.8, 0.86, 1.87, 0.36, 2.26, 2.33, 1.84000003, 1.88, 1.91999996, 1.93, 1.6, 1.51, 0.75, 5.6, 1.0, 1.98, 1.4, 4.6, 0.78, 1.13, 3.28, 1.29, 1.21, 1.0, 1.23, 0.63, 1.27, 0.85, 1.42, 0.1, 4.9, 2.1, 2.00999999, 2.04999995, 5.4, 5.3, 2.12, 2.6, 0.3, 1.2, 0.45, 1.57, 0.2, 2.4, 2.2, 1.3, 4.7, 0.77, 1.97000003, 1.3, 2.04, 0.35, 0.44, 4.2, 2.0, 0.75, 1.7, 1.14, 0.71, 1.2, 2.1099999, 2.04999995, 1.2, 0.55, 1.01, 0.44, 3.52, 0.98, 1.04, 1.26, 0.63, 0.35, 1.77, 2.5, 1.5, 1.79, 0.86, 1.3, 1.5, 0.4, 0.51, 2.0, 0.18, 0.8, 1.9, 2.3, 1.99000001, 1.77, 1.39, 0.95, 4.5, 0.06, 0.89, 1.1, 2.3, 1.9, 0.6, -0.46, 0.49, 1.84, 1.39, 2.54, 0.63, 1.16, 1.4, 1.86000001, 2.22, 3.0, 1.56, 1.3, 1.14, 1.89, 1.99000001, 1.72, 1.7, 0.84, 5.0, 1.86000001, 1.3, 0.84, 1.13, -0.36, 1.4, 2.1, 1.61, 1.51, 0.78, 5.3, 2.1, 1.85, 0.03, 1.71, 0.76, 2.0, 4.7, 1.7, 1.2, 2.25, 1.81, -0.14, 1.4, 0.09, 4.6, 2.04, 1.15, 0.84, 1.6, 0.29, 1.8, 1.1, 2.2, 0.73, 3.7, 1.26, 1.06, 4.6, 1.44, 1.43, -0.29, 3.1, 1.92, 1.81, 1.14, 0.36, 1.6, 1.4, 4.4, 1.25, 1.18, 2.12, 1.69, -0.13, 0.85, 0.69, 1.17, 1.1, 4.5, 1.3, 2.19000006, 4.3, 1.0, 1.69, 1.85, 1.3, 2.6, 4.8, 1.4, 4.2, 4.9, 1.5, 1.4, 1.31, 1.2, 0.77, 0.58, 4.4, 1.4, 4.3, 1.8, 1.83, 1.74000001, 0.51, 1.1, 1.84, 3.77, 0.92, 1.4, 2.41, 4.4, 2.7, 0.81, 2.15, 4.1, 4.6, 2.25999999, 2.1500001, 1.2, 2.05, 2.3, -0.73, 1.68, -0.94, 0.28, 1.4, 4.5, 0.35, 1.19, 1.2, 1.7, 0.67, 1.83000004, 1.43, 0.9, 2.73, 1.4, 4.0, -0.5, 1.9, 1.17, 1.19, 1.81, 2.55, 0.31, 2.41, 1.06, 0.85, 5.2, 1.9, 2.5, 4.9, 1.18, 1.86, 0.36, 0.86, 2.4, 1.11, 0.5, 1.61, 1.17, 4.3, 1.7, 1.0, 0.84, 0.91, 0.95, 1.98, 3.1, 0.36, 0.36, 1.2, 2.21, 2.21, 0.86, 1.38, 2.04, 0.6, 1.1, 1.4, 2.3499999, 0.8, 1.18, 1.22, 1.99000001, -0.33, 4.8, 3.21, 1.19, 1.5, 1.1, 1.07, 1.04, 0.96, 0.45, 0.6, 0.9, 1.07, 2.41, 2.33, 4.5, 0.9, 0.7, 0.26, 4.9, 1.6, 0.51, 0.26, 4.1, 2.26, 2.64, 4.9, 0.6, 1.99, 4.8, 1.28, 0.84, 3.69, 1.7, 4.2, 1.1, 2.33, 1.5, 4.3, 2.05999994, 2.66, 1.9, 5.4, 0.68, 0.59, 0.9, 2.1500001, 0.61, 2.04999995, 1.4, 1.42, 1.44, 2.9, 1.01, 0.9, 1.88, 1.85, 0.77, 2.78, 0.58, 1.03, 1.1, 0.86, 0.6, 1.43, 2.41000009, 1.9, 0.94, 0.7, 2.6, 0.85, 2.74, 1.22, 4.1, 2.1, 1.32, 0.88, 2.34, 1.9, 1.13, 0.32, 0.83, 1.2, 1.61, 1.6, -0.2, 0.76, 0.36, 1.39, 1.61, 2.2, 1.41, 2.6, 1.96, 1.18, 1.7, 2.08, 2.5, 0.05, 1.92, 2.9, 2.0, 1.51, 2.7, 1.01, 0.52, 1.61, 2.0, 1.42, 2.6, 1.8, 1.1, 1.3, 1.6, 2.07999992, 0.82, 1.8, 0.82, 1.66, 3.61, 0.48, 2.21000004, 4.5, 1.8, 0.0, 0.8, 1.26, 0.94, 4.4, -0.32, 0.84, 1.77, 0.64, 1.42, 1.19, 0.0, 1.91999996, 0.86, 1.75, 1.68, 1.23, 1.19, 0.85, 0.72, 2.3, 3.69, 2.4, 1.8, 1.42, 1.11, 0.53, 1.69, 1.41, 5.5, 2.31, 3.99, 2.16000009, 3.18, 1.16, 3.2, 4.9, 0.92, 1.75, 0.8, 0.86, 2.8, 1.66, 0.59, 1.4, 1.46, 4.8, 0.9, 1.4, 1.01, 3.15, 0.8, 1.59, 1.84, 0.67, 1.48, 1.5, 0.85, 1.27, 2.3, 0.85, 1.19, 0.36, 4.3, 1.19, 1.61, 2.1, 2.0, 1.2, 1.99, 1.57, 1.8, 1.9, 1.19, 1.0, 1.67, 0.57, 0.88, 4.8, 1.75, 1.18, 1.34, 0.54, 4.4, -0.45, 4.5, 4.5, 2.17, 1.9, 2.99, 0.93, 1.07, 4.4, 2.2, 4.8, 2.1, 2.3, 0.54, 1.0, -0.2, 4.4, 2.0, 1.95000005, 4.3, 0.29, 2.2, 4.6, 0.11, 2.1, 0.87, 1.83, 2.2, 2.38, 1.88, 4.2, 1.42, 4.5, 0.72, 0.46, 0.67, 1.8, 2.24, 1.8, 1.96, 0.74, 0.52, 0.39, 0.45, 1.2, 4.4, 4.1, 0.8, 0.7, 0.9, 1.4, 0.88, 1.5, 0.87, 2.05999994, 2.56, 1.9, 1.48, 1.91, 0.9, 0.54, 1.6, -0.3, 3.9, 4.2, 1.98000002, 0.21, 4.3, 0.62, 4.4, -0.2, 1.6, 1.39, 4.5, 1.8, 1.1, 0.57, 0.35, 0.3, 4.4, 1.6, 4.3, 1.0, 1.2, 2.0, 1.46, 0.34, 2.33, 1.97, -0.3, 1.8, 0.67, 0.65, 2.0, 1.6, 4.2, 0.85, 3.4, 1.4, 1.46, 1.3, 1.17, 1.8, 1.87, 4.7, 1.61, 0.91, 0.35, 1.04, 0.97, 2.0, 0.45, 0.34, 0.85, 0.36, 2.43, 2.27, 4.5, 0.86, 2.54, 0.85, 1.12, 1.1, 1.25, 1.75999999, 2.6, 1.97, 2.1, 1.17, 0.54, 2.62, 2.1, 0.8, 0.85, 0.35, 0.42, 0.86, 0.95, 2.21000004, 3.7, 1.49, 2.25, 0.7, 0.97, 1.22, 1.53, 0.85, 1.42, 0.69, 1.85000002, 1.79, 1.7, 1.49, 1.8, 2.16000009, 1.61, 1.3, 4.1, 1.87, 1.7, 0.84, 2.14, 0.9, 1.72, 2.17, 2.3, -0.73, 1.97000003, 2.98, 1.73, 1.7, 1.48, -0.4, 2.83, 0.97, 2.97, 3.0, 1.8, -0.59, 0.84, 1.5, 0.67, 1.39, 1.9, 1.25, 0.86, 1.53, 1.48, 0.9, 1.16, 0.9, 0.52, 0.85, 0.57, 4.6, 2.7, 1.3, 1.66, 0.05, 0.91, 4.4, 2.56, 0.85, 1.17, 1.28, 5.2, 0.84, 2.8, 0.37, 4.2, 2.0, 4.5, 1.4, -0.28, 1.5, 4.8, 4.5, 1.77, 0.84, 0.74, 4.5, 1.19, 1.9, 1.51, 2.67, 1.02, 1.36, 0.82, 2.25999999, 2.0, 2.33, 4.8, 0.36, 4.9, 1.86, 0.09, 0.5, 1.53, 1.92999995, 1.7, 0.53, 0.7, 0.83, 1.6, 2.03, 1.42, 2.39, 1.4, 0.71, 0.92, 1.8, 1.73, 1.27, 0.75, 1.36, 0.4, 1.66, 2.27, 0.85, 1.75, 1.92, 2.1, 2.38, 1.04, 2.04999995, 4.6, 0.37, 4.3, 4.4, 1.9, 1.89999998, 1.4, 0.36, 1.21, 1.36, 0.4, 3.52, 1.6, 1.7, 0.42, 2.3599999, 0.68, 4.4, 0.92, 2.3, 0.84, 2.6, 0.97, 0.54, 2.19, 1.4, 0.82, -0.11, 2.0, 2.0, 1.52, 2.4, 0.6, 1.73, 2.72, 0.19, 0.79, 2.1, 4.3, 0.75, 2.2, 1.3, 0.54, 1.45, 1.65, 1.71, 0.87, 2.41, 1.9, 2.05, 1.9, 1.8, 0.45, 2.68, 1.52, 0.45, 2.5, 1.03, 1.44, 1.06, 4.7, 1.8, 2.9, 1.4, 2.42, 4.9, 2.3, 1.03, 1.73, 1.59, 0.36, 1.6, 2.56, 4.7, 4.6, 0.63, 1.86000001, 2.0, 0.11, 0.38, 1.3, 0.64, 0.29, 1.25, 4.0, 1.13, -0.45, 0.81, 1.75999999, 1.94, 1.36, 2.5, 2.0, 2.17, 1.17, 0.23, 1.18, 0.59, 2.6, 1.61, 0.2, 0.84, 1.37, 2.5, 1.12, 1.2, -0.77, 0.11, 1.65, 1.62, 1.15, 0.76, 3.32, 1.27, 0.85, 2.09, 2.2, 1.1, 0.44, 1.71, 0.97, -0.11, 1.88, 0.28, 1.4, 3.7, 1.62, 2.1500001, 0.07, 1.89, 0.7, 1.6, 2.3, 1.18, 1.43, 1.5, 2.04999995, 1.9, 1.0, 2.67, 1.48, 1.4, 0.62, 1.44, 1.17, 2.8, 0.47, 1.4, 2.27, 1.34, 2.02, 0.51, 2.0, 1.49, 5.6, 1.1, 0.83, 1.6, 2.1400001, 0.92, 0.38, 1.07, 2.8, 1.9, 1.89, 1.67, 1.29, 0.87, 1.0, 1.8, 1.56, 1.1, 2.87, 3.06, 2.16, 4.2, 1.43, 1.89999998, 0.86, 1.4, 1.92999995, 2.29, 1.91, 1.01, 0.71, 1.7, 2.0, 2.11999989, 1.87, 0.5, 2.0, 1.99000001, 0.94, 1.51, 1.0, 1.1, 0.04, 1.0, 1.38, 0.78, 1.0, 0.9, 0.46, 2.14, 0.53, 1.07, 1.53, 4.1, 0.85, 0.85, 0.61, 0.5, 1.51, 1.3, 0.84, 1.12, 1.9, 1.4, -0.19, 1.93, 1.8, 2.1, 4.3, 1.4, 1.08, 0.23, 1.59, 1.4, 1.58, 1.41, 1.6, -0.13, 4.9, 4.3, 1.88, 4.6, 0.84, 2.9, 1.4, 1.75999999, 0.36, 0.64, -0.04, 1.46, 0.86, 1.9, 2.6, 1.67, 1.17, 2.0, 0.9, 1.28, -0.33, 1.5, 0.37, 1.3, 0.59, 0.85, 0.8, 1.36, 1.1, 2.26, 0.92, 1.90999997, 1.1, 3.62, 0.71, 4.4, 2.16, 1.7, 4.7, 1.9, 1.8, 4.0, 0.78, 2.6, 0.84, 1.15, 1.41, 0.9, 0.8, 1.43, 5.1, 0.41, 1.08, 1.48, 1.4, 1.99, 2.06, 2.0, 1.54, 0.88, 1.6, 1.2, 1.74, 1.56, 1.5, 1.7, 1.09, 0.35, 1.2, 2.75, 0.31, 0.5, -0.08, 0.6, 0.81, 2.26, 0.48, 1.3, 2.71, 0.49, 1.87, 0.82, 1.7, 1.0, 1.92, 0.89, 2.61, 4.7, 1.8, 4.2, 0.8, 0.9, 0.81, 1.6, 1.6, 1.57, 0.52, 5.4, 0.36, 1.5, 0.22, 1.28, 0.89, 1.4, 1.49, 1.49, 0.9, 5.1, 0.9, 1.0, 2.06, 0.9, 0.8, 1.17, 0.22, 2.83, 0.99, 0.85, 0.18, 2.27, 0.85, 2.04, 0.85, 1.0, 4.5, 0.85, 1.1, 1.82, 1.84000003, 5.6, 1.55, 1.4, 0.2, 0.97, 2.1500001, 1.72000003, 0.86, 2.09, 1.59, 0.99, 1.42, 1.89999998, 1.04, 0.43, 1.5, 2.1, 0.92, 1.59, 1.9, 1.6, 1.18, 1.91999996, 2.0, 1.86000001, 0.48, 0.88, 1.35, 0.43, 0.89, 0.89, 0.84, 2.37, 0.16, 1.81, 5.0, 1.05, 4.9, 1.03, -0.01, 1.18, 1.58, 1.0, 0.37, 1.17, 0.81, 4.1, 1.18, 0.36, 4.4, 1.46, 1.7, 2.23, 1.15, 2.0, 0.6, 1.05, 1.21, 0.3, 1.76999998, 1.0, 1.49, 3.0, -0.3, 1.19, 0.71, -0.02, 0.01, 0.54, 1.48, 1.94, 2.8, 2.22, 0.72, 4.2, 0.34, 4.6, 0.88, 2.2, 0.37, 0.82, 2.0, 2.12, 1.72, -0.23, 1.54, 0.17, 0.14, 1.2, 0.9, 1.5, 2.1, 1.3, 1.21, 2.57, 1.27, 0.83, 0.45, 1.7, 0.8, 0.41, 1.86, 2.4, 0.03, 2.22, 0.38, 0.84, 2.3, 1.74, 1.69, -0.63, 3.39, 3.41, 0.2, 1.58, 1.3, 3.75, 1.1, 1.18, 1.69, 0.88, 4.6, 1.28, 2.6, 3.12, 1.37, 1.43, 1.25, 0.62, 0.38, 0.53, 2.69, 0.85, 3.17, 1.4, 0.84, 0.75, 1.35, 0.63, 1.84000003, 0.93, 0.74, 2.93, 1.8, 2.81, 1.68, 1.01, 0.9, 1.49, 1.37, 0.6, 4.6, 2.0, 2.0999999, 4.7, 0.77, 1.4, 1.2, 1.8, 1.73, 1.9, 1.01, 1.49, -0.23, 0.73, 1.1, 1.4, 1.4, -0.07, 4.4, 2.36, 4.7, 4.4, 1.6, 4.5, 4.6, 1.95000005, 0.01, 1.29, 1.3, 2.43, 1.76, 1.82000005, 1.2, 0.85, 0.34, 1.3, 2.43, 4.4, 2.37, 0.79, 4.3, 1.62, 0.8, 2.38, 1.25, 0.8, 5.4, 5.3, 1.07, 0.5, 1.74, 1.22, 1.02, 0.73, 1.18, 0.71, 5.6, 0.71, 0.37, 2.6, 1.2, 1.32, 1.14, -0.53, 1.58, 1.5, 4.2, 1.16, 1.12, 1.66, 3.35, 1.1, 2.2, 0.45, 3.5, 2.11, 1.74000001, 0.95, 1.7, 1.6, 0.97, 1.6, 1.74, -0.35, 2.8, 1.27, 1.8, 0.85, 2.34, 0.77, 1.7, 1.3, 1.04, 0.98, 1.18, 1.67, 1.9, 0.9, 1.66, 0.21, 1.06, 1.9, 0.87, 0.39, 0.76, 1.4, 1.35, 0.85, 4.4, 0.57, 2.65, 0.52, 0.33, 1.2, 4.4, 4.6, 0.95, 1.39, 0.84, 4.2, 0.35, 1.2, 0.3, 1.2, 1.13, 1.65, 0.51, 2.17, 0.8, 4.8, 1.4, 1.5, 4.8, 1.43, 1.21, 2.03, 1.7, 0.63, 1.28, 0.32, 1.1, 0.98, 1.6, 1.6, 2.25, 5.1, 0.47, 1.16, -0.7, 1.94, 2.32, 1.95000005, 0.25, 0.92, 2.2, 1.88, 1.3, 1.2, 2.5, 1.28, 1.99000001, 2.7, 1.74, 1.75, 2.68, 0.25, 0.65, 1.51, 1.42, 4.9, 1.57, 0.2, 1.6, 4.3, 2.1400001, 0.36, 0.44, 1.6, 0.91, 1.03, 1.47, 1.48, 1.27, 0.3, 1.89999998, -0.2, 1.22, 0.41, 1.93, 1.4, 2.28, 1.66, 0.35, 3.0, 1.11, 0.3, 1.3, 1.57, 1.7, 2.2, 1.35, 1.56, 1.27, 0.18, 2.11, 1.7, 0.86, 4.6, 0.36, 0.83, 1.0, 0.86, 0.69, 1.54, -0.06, 1.93, 0.64, 2.63, 2.1500001, -0.37, 1.5, 1.74, 4.2, 1.5, 1.75, 0.36, 0.84, 1.69, 1.93, -0.02, 2.18, 0.99, 2.42, 2.23, 1.8, 1.99000001, 0.85, 4.3, 1.22, 0.56, 1.71, 1.05, 1.24, 0.61, 0.5, 0.37, 2.37, 1.35, 2.4, 0.99, 0.46, 1.14, 2.2, 0.36, 1.07, 0.51, 0.85, 0.83, 1.42, 0.82, 0.36, 1.01, 4.5, 3.1, 3.1, 1.49, 0.63, 1.94, 1.56, -0.17, 1.05, 1.9, 0.85, 1.12, 1.15, 3.42, 2.0, 1.12, 2.07, 2.0, 1.18, 0.02, 1.4, 2.27, 3.6, 2.1, 0.82, 1.99000001, 2.29999995, 1.99000001, 2.21000004, 0.56, 1.8, 2.4, 2.0, 1.93, 0.85, 1.4, 1.8, 0.37, 4.3, 1.51, 1.47, 1.3, 2.7, 1.12, 0.1, 1.6, 0.9, 1.6, 0.88, -0.09, 1.3, 1.18, 2.7, 0.76, 1.1, 2.0, 0.46, 1.05, 0.68, 0.36, 2.29999995, 2.0, 0.14, 0.83, 0.63, 1.26, 1.76999998, 2.14, 1.5, 1.03, 1.5, 1.69, 0.8, 1.5, 2.07, 2.01, 2.25, 2.00999999, 0.15, 1.9, 1.4, 3.63, 0.41, 0.66, 5.2, 1.6, 1.88, 1.12, 0.57, 1.55, 4.4, 0.88, 4.4, 1.4, 0.98, 1.2, 0.85, 1.0, 2.1500001, 0.35, 1.4, 0.36, 1.92, 0.97, 2.03999996, 0.5, 0.85, 0.58, 3.55, 0.91, 0.23, 0.21, 0.9, 2.3, 2.2, 4.5, 0.38, 1.37, 0.84, 0.84, 2.04, 1.36, 0.24, 1.86, 4.6, 1.5, 2.18, 2.3, 4.4, 1.8, 1.55, 0.01, 4.3, 2.93, 5.0, 2.1, 1.13, 0.85, 1.54, 2.2, 0.46, 1.82000005, 4.7, 0.9, 4.5, 2.1, 2.2, 0.2, 5.0, 5.8, 0.2, 2.2, 2.1400001, 2.18, 2.0, 0.55, 4.4, 1.34, 1.92999995, 0.99, 1.5, 1.49, 2.25, 1.16, 5.4, 1.99000001, 1.25, 1.9, 1.7, 1.0, 1.44, -0.2, 2.9, 2.9, 2.0, 1.7, 3.6, 4.7, 6.2, 2.48, 3.8, 1.84, 1.79, 1.81, 1.7, 1.9, 1.1, 1.3, 1.42, 2.36, 0.8, 0.76, 1.79, 0.29, 1.42, 0.64, 1.18, 0.65, 0.46, 0.88, 0.75, 1.0, 1.66, 1.45, 2.26, 0.35, 0.86, 1.34, 1.62, 1.18, 1.69, 0.85, 0.94, 0.03, 1.42, 1.3, 1.48, 0.87, 1.25, 4.5, 1.75, 1.03, 1.83000004, 2.02, 2.8, 1.49, 5.2, 0.84, 2.02999997, 4.3, 0.98, 1.9, 0.86, 0.9, 2.5, 0.94, 1.53, 2.0, 0.6, 0.75, 2.3, 1.59, 0.16, 0.85, 1.1, 0.7, -0.01, 1.09, 1.77, 2.59, 0.78, 2.87, 2.64, 1.85000002, 4.4, 2.34, 1.71, 1.55, 0.89, 4.9, 0.85, 0.76, 1.05, 1.5, 2.6, 0.57, 0.85, 0.6, 0.33, 1.85000002, 1.0, 1.49, 0.85, 4.9, 0.3, 0.54, 0.21, 1.89999998, -0.21, 1.3, 1.3, 0.35, 0.37, 1.26, 2.1, 4.4, 4.1, 0.7, 4.0, 0.79, 1.15, 4.5, 0.7, 3.34, 0.91, 0.03, 0.6, 2.53, 1.1, 1.2, 2.15, 3.22, 1.3, 4.3, 0.6, 3.9, 0.21, 1.88, 0.88, 4.0, 1.02, 3.09, 0.62, 0.9, 1.5, 0.85, 1.93, 1.74, 1.87, 2.29, 3.21, 1.0, 2.6, 1.13, 2.18, 0.04, 0.86, -0.35, 1.14, 2.74, 2.67, 4.5, 0.8, 1.09, 2.5, 1.84, 1.5, 1.5, 2.04999995, 1.83, 1.06, 0.74, 1.9, 2.72, 0.86, 1.57, 0.8, 0.1, 0.9, 4.9, 4.2, 4.4, 1.83000004, 3.9, 2.2, 4.1, 0.56, 1.07, 4.2, 0.54, 0.97, 2.32, 0.37, 1.12, 0.84, 1.15, 0.62, 1.42, 0.0, 1.83, 2.4, 1.52, 1.5, 1.46, 0.79, 2.4, 3.0, 5.5, 1.97, nan, 2.4, 1.9, 4.3, 2.15, 0.14, 1.79, 1.7, 0.79, 1.49, 1.43, 1.5, 1.5, 1.0, 1.02, 1.9, 0.21, 1.51, 1.56, 1.63, 0.84, 0.7, 1.75, 2.03, 1.7, 1.43, 2.02, 1.09, 1.0, 3.8, 1.36, 0.88, 1.52, 1.15, 2.98, 1.15, 1.71, 2.1, 2.26, 1.84000003, 1.2, 2.12, 2.55, 3.22, 3.86, 0.95, 1.79, 4.9, 4.9, 1.7, 0.33, 2.26, 2.6, 4.1, -0.05, 2.35, 1.92999995, 1.79, 1.94, 2.13000011, 1.91, 0.05, 4.5, -0.08, 1.92999995, 0.64, 0.9, 1.46, 1.53, 2.23, 0.84, 0.85, 0.86, 2.04999995, 0.35, 4.3, 2.21000004, 2.3, 1.5, 0.85, 4.6, 3.39, 1.64, 4.9, 1.5, 2.27, 2.2, -0.25, 0.48, 1.39, 4.3, 1.84000003, 1.03, 1.6, 1.79, 4.6, -0.07, 1.8, -1.21, 0.8, 0.32, 1.68, 2.06, 4.8, 0.93, 2.63, 4.3, 0.55, 1.28, 2.41, 1.5, 3.0, 1.91, 4.8, 0.9, 1.84000003, 0.59, 1.18, 0.7, 1.7, -0.11, -0.45, 1.37, 4.1, 1.9, -0.18, 0.18, 1.5, 1.0, 0.95, 1.21, 1.69, 0.13, 4.3, 1.92999995, 1.99, 2.5, 2.5, 1.72, 2.56, 2.5, 2.6, 1.84000003, 1.83000004, 1.08, 0.85, 2.06, 1.12, 1.26, 1.2, 1.46, 1.3, 4.2, 0.47, 1.8, 1.0, 2.2, 0.72, 1.75, 0.53, 1.18, 1.19, 1.9, 0.96, 1.9, 1.76, 1.6, 4.9, 1.25, 1.11, 1.8, 0.9, 0.91, 1.69, 5.3, 0.84, 1.03, 0.92, 0.84, 0.35, -0.04, 2.39, 2.39, -0.15, 2.17, 4.5, 0.2, 1.70000005, 1.78, 2.1099999, 0.4, -0.3, 1.12, 2.0, 5.0, 1.63, 2.38, 1.77, 1.47, 1.84, 1.3, 1.62, 1.0, 1.2, 1.5, 0.2, 1.7, 1.86000001, 1.85000002, 1.71, 2.66, 0.43, 0.42, 0.58, 1.62, -0.63, 3.2, 0.4, 0.84, 1.17, 2.09, 1.80999994, 4.9, 2.4, 2.35, 2.7, 1.92999995, 0.77, 1.69, 1.28, 1.8, 4.0, 1.21, 0.01, 2.64, 1.91, 1.34, -0.2, 0.5, 0.61, 4.9, 0.88, 2.24, 0.54, 0.2, 1.5, 0.85, 1.18, 1.96, 1.85000002, 4.3, 1.89, 2.4, 2.41000009, 0.19, 2.54, 1.7, 0.85, 2.1, 2.21, 1.99, -0.18, 1.6, 1.08, 0.36, 4.2, 1.39, 2.51, 2.42, 0.84, 0.9, 1.4, 0.63, 1.89999998, 4.4, 2.2, 0.42, 1.3, 1.79, 1.77, 1.65, 1.95000005, 4.7, 0.9, 0.36, 0.6, 0.71, 0.31, 0.94, 4.2, 1.99, 1.99, 0.6, 1.56, 1.07, 1.2, 0.36, 0.65, 1.9, 1.47, 0.85, 0.05, 0.87, 2.1, 0.67, 0.63, 1.3, 0.35, 2.36, 0.13, 1.5, 0.8, 1.63, 1.72000003, 0.36, 0.25, 1.53, 1.3, 1.18, 1.32, 2.3, 1.3, 1.81, 1.58, 0.24, 0.88, -0.2, 2.2, 1.89, 3.68, 0.86, 3.33, 0.56, 0.35, 0.85, 0.49, 1.5, 1.6, 2.74, 3.06, 2.59, 0.4, 2.13, 2.38, 0.34, 0.35, 0.7, 1.49, 2.4, 4.4, 4.6, 1.4, 0.37, 1.38, 1.03, -0.47, 3.13, 0.41, -0.1, 1.51, 4.4, 1.86000001, 1.09, 2.57, 4.1, 1.85000002, 2.24000001, 1.28, 2.25999999, 0.65, 2.05, 2.4, 1.8, 4.8, 0.89, 1.3, 0.85, 2.02999997, 1.86, 1.6, 1.6, 0.84, 0.82, 1.07, 1.86000001, 1.4, 0.95, 2.13, 2.9, 0.6, 2.1, 2.06999993, 2.0, 0.36, 0.84, 1.98000002, 0.6, 0.47, 1.01, 2.19, 0.86, 2.7, 2.7, 4.0, 1.93, -0.22, 2.0, 1.39, 1.37, 1.28, 1.64, 1.19, 1.05, 0.86, 0.13, 4.3, 0.0, 0.5, 1.89, 2.29, 3.5, 2.03999996, 0.83, 0.86, 0.89, 1.2, 4.1, 2.97, 4.6, 1.1, 2.24, 0.52, 0.84, 1.55, 1.63, 2.6, 0.39, 0.85, 3.83, 1.1, 2.08999991, 0.44, 1.49, 1.99, 0.93, 1.74, 0.78, 3.5, 5.3, 0.78, 2.2, 1.22, 0.84, 2.0, 0.85, 4.5, 1.7, 1.86000001, 2.63, 1.57, 4.6, 0.84, 4.2, 1.3, 0.58, 1.34, 2.18, 1.49, 1.42, 2.03999996, 3.43, 0.84, 0.1, 1.3, 0.09, 2.5, 0.84, 1.3, 1.45, 4.3, 1.69, 5.0, 4.2, 2.2, 2.1, 1.1, 2.59, 1.2, 0.6, 0.85, 0.86, 1.4, 2.74, 1.29, 1.53, 1.81, 2.1, 2.1, 0.83, 4.8, 0.36, 1.35, 0.73, 1.2, 1.2, 0.44, 4.3, 2.2, 1.83, 1.7, 0.06, 0.8, 0.18, 1.71, 0.38, 4.3, 1.21, 1.9, 0.58, 0.35, 1.4, 1.3, 0.9, 4.3, 3.51, 2.0, 1.8, 1.32, 0.43, 1.72, 1.8, 1.1, 1.37, 0.71, 1.39, 0.63, 1.9, 0.4, 0.37, 2.43, 1.91, 0.5, 0.72, 1.2, 0.36, 1.18, 1.48, 1.7, 2.3, 0.87, 1.16, 1.27, 0.65, 2.0, 1.32, 1.05, 0.66, 0.36, 1.18, 1.25, 0.94, 2.1, 3.1, 1.66, 2.08999991, 1.5, 2.16000009, 2.51, 0.78, 0.07, 0.35, 0.9, 1.1, 0.69, 1.1, 1.29, 0.9, 0.54, 0.74, 1.86, 1.01, -0.75, 1.5, 0.7, 2.62, 1.02, 2.0999999, 0.54, 0.38, 1.6, 1.79, 2.5, 1.08, 1.06, 2.1, 3.4, 0.56, 0.36, 1.8, 0.23, 0.75, 0.67, 1.73000002, 4.6, 1.2, 4.1, 0.39, 1.74, 0.28, 2.03999996, 1.67, 0.8, 4.3, 1.52, 2.53, 2.4, 2.42, 1.6, 1.74, 0.11, 1.94, 0.8, 4.6, 1.1, 1.47, 1.57, 0.02, 2.6, 0.95, 4.6, 2.19000006, 1.70000005, 1.5, 0.98, 1.86, 2.1099999, 1.28, 0.2, 4.7, 1.94000006, 2.14, 2.08999991, 1.17, 2.34, 1.4, 0.98, 1.72000003, 4.8, 2.4, 0.69, 1.7, 0.68, 1.06, 1.6, 2.34, 0.86, 0.67, 1.85000002, 2.23, 1.44, 0.56, 1.73, 0.85, 1.3, 1.57, 1.77999997, 1.03, 2.0, 1.31, 0.0, 0.44, -0.11, 1.4, 0.55, 2.24000001, 1.66, 1.81, 1.9, 0.71, 1.87, 1.4, 1.58, 4.4, 1.15, 1.24, 1.6, 0.62, 2.24, 1.5, 1.76, 4.4, 2.02999997, 1.99000001, 1.4, 2.27, 1.1, 1.87, 1.44, 4.4, -0.3, 0.1, -0.16, -0.3, 0.47, 4.2, -0.51, 0.0, 0.89, -0.2, 1.73, 4.5, 1.83000004, -0.53, 1.89, 4.4, 0.8, 2.33, 1.25, 4.3, 0.65, 2.7, 0.5, 1.5, 1.1, 1.4, 4.6, 0.86, 1.07, 2.22000003, 2.01, -0.07, 4.2, 1.9, 0.88, 0.85, 1.89, 1.9, -0.08, 2.25, 2.8, 1.6, 2.1, 1.5, 0.53, 0.48, 1.3, 0.33, 4.4, 1.26, 5.2, 4.1, 0.95, 4.1, 2.47, 1.0, 0.69, 1.28, 1.3, 4.3, 1.86, 0.94, 2.3, 1.96, -0.3, 1.8, 1.82000005, 1.6, 2.2, 0.35, -0.1, 0.7, 0.88, 1.2, 4.4, 0.9, 0.48, 1.22, 1.64, 0.2, 1.84000003, 1.44, 0.87, 0.78, 1.04, 1.71, 2.01, 2.04999995, 1.0, 0.3, 1.6, 0.21, 4.3, 2.0, 1.9, 0.37, 4.4, 2.18000007, 0.5, 1.28, 1.2, 0.86, 1.16, 0.72, 0.0, 2.3, 1.0, 1.0, 0.8, 0.98, 1.16, 0.9, 0.37, 1.06, 1.4, 1.32, 2.0, 1.83, 0.52, 0.81, 0.23, 2.1, 0.97, 2.04, 0.85, 4.1, 0.5, 5.2, 0.97, 0.68, 3.17, 4.4, 1.45, 2.7, 1.13, 1.4, 2.6, 1.6, 1.3, 0.46, 0.6, 0.36, 1.7, -0.1, 1.9, 0.66, 2.16000009, 2.3, 0.01, 1.5, 2.3, 1.16, 1.88999999, 1.78, 1.4, 0.39, 2.54, 0.65, 0.41, 1.72000003, 5.3, 2.33999991, 1.21, 0.7, 2.4, 0.86, 2.11, 1.6, 1.85000002, 2.24, 1.59, 0.35, 0.99, 1.70000005, 0.85, 2.87, 1.19, 1.3, 4.5, 1.42, 1.0, 0.44, 1.88, 1.55, 0.63, 0.67, 4.9, 1.64, 0.6, 0.88, 0.84, 0.91, 0.76, 0.92, 2.6, 0.46, 1.3, 1.4, 4.7, 4.4, 1.4, 3.1, 6.0, 1.4, 1.5, 2.26999998, 1.91, 0.76, 0.36, 1.1, 1.62, 0.72, 2.84, 0.67, 1.9, 4.2, 0.58, 1.56, 4.2, 1.7, 1.33, 4.2, 1.5, 0.21, 1.8, 2.08999991, 0.22, 2.1500001, 1.51, 0.5, 1.7, -0.05, 2.0, 0.7, 4.6, 0.85, 0.66, 4.1, 0.3, 1.7, 2.1, 4.0, 3.3, 2.00999999, 0.85, 0.91, 4.5, 4.5, 0.83, 1.9, 1.73, -0.03, 0.42, 0.64, 1.3, 2.17000008, -0.32, 1.4, 0.57, 1.7, 2.17000008, 2.1400001, 1.99000001, 4.6, 0.83, 1.6, 1.09, 2.24000001, 0.8, 4.1, 0.83, 0.23, 4.6, 0.71, 1.62, 2.52, 0.32, 2.31, 1.37, 0.14, 2.37, 1.9, 0.98, 2.03999996, 1.9, 1.34, 0.89, 0.95, 0.6, 1.19, 5.2, 0.81, 4.1, 2.13000011, 2.0999999, 1.19, 2.5, 0.63, 0.73, 2.7, 0.5, 1.19, 1.2, 4.8, -0.23, 0.35, 1.43, 0.85, 4.9, 2.22000003, -0.14, 1.4, 0.66, 2.6, 1.6, 1.4, 1.42, -0.15, 4.6, 1.1, 2.04999995, 2.33, 1.92, 0.76, 0.9, 0.4, 2.34, 0.6, 0.99, 1.4, 0.92, 4.2, 1.87, 0.9, 4.6, 0.67, 1.36, 2.54, 0.86, 0.58, 4.5, 1.0, 2.38, 1.85, 1.3, 2.7, 1.5, 1.5, 3.97, 0.36, 4.7, 1.4, 1.96, 0.86, 0.18, 4.1, 3.03, 4.4, -0.33, 1.92, 2.12, 0.85, 0.91, 4.6, 0.38, 4.5, 1.67, 4.4, 0.65, 0.21, 1.95000005, 4.4, 1.28, 2.1099999, 1.5, 4.4, 2.4, 0.85, 4.2, 0.89, 1.9, 4.8, 2.5, 4.0, 0.9, 2.0, 4.1, 1.68, 4.0, 0.99, 0.42, 4.5, 4.6, 4.4, 5.0, 2.0, 4.4, 0.48, 4.1, 2.4, 1.93, 4.4, 4.4, 1.38, 1.31, 1.1, 2.4, 0.7, 6.3, 6.0, 0.79, 0.92, 1.2, 5.0, 1.74000001, 1.80999994, 0.32, 0.2, 1.73, 2.4, 0.7, 0.86, 0.8, 1.5, 2.0, 0.7, 3.17, 0.15, 0.3, 1.74, 0.86, 0.63, 0.09, 2.22, 2.84, 1.18, 1.0, 0.9, 2.04999995, 2.07999992, 1.36, 0.36, 0.7, 0.5, 0.87, 1.27, 1.54, 1.18, 1.56, 1.3, 1.7, 0.62, 0.85, 0.82, 1.29, 1.16, 1.07, 1.28, 1.15, 1.9, 1.91999996, 1.41, 0.8, 1.43, 1.26, 0.93, 0.37, 0.76, 2.6, 1.3, 2.5, 2.3, 0.64, 0.89, 1.58, 1.7, 1.3, 1.15, 1.2, 4.9, 2.51, 1.01, 1.43, -0.02, 0.4, 0.62, 2.11, 1.6, 1.07, 1.4, 1.85000002, 1.3, 0.85, 0.5, 0.45, 0.62, 1.49, 2.58, 0.85, 1.62, 0.58, 1.46, 0.53, 1.2, 4.2, 4.1, 1.9, 1.4, 2.1, 1.81, 1.71000004, 4.1, 1.1, 4.7, 0.59, 4.8, 1.98, 4.6, 4.5, 1.8, 4.5, 1.4, 0.62, 2.3, 4.1, 5.1, 0.88, 1.22, 0.46, 0.54, 1.3, 0.62, 4.4, 3.67, 2.6, -0.32, 0.54, 0.82, 1.5, 0.31, 1.12, 1.1, 2.4, 4.4, 1.2, 1.4, 0.07, 0.84, 1.01, 2.6, -0.18, 2.3, 0.7, 4.6, 1.46, 0.9, 0.8, 1.6, 4.4, 0.01, 4.3, 1.1, 1.91, 0.3, 1.25, 0.7, 5.4, 0.38, 1.78999996, 2.44, 4.8, 2.13, 4.5, 0.85, 0.73, 1.91, 4.1, 0.91, 2.3, 0.47, 4.7, 0.45, 0.35, 1.6, 2.07, 2.22, 0.55, 1.05, 1.1, 1.7, 4.9, 4.2, 1.13, 3.0, 4.7, 1.53, 2.59, 1.91, 1.4, 0.57, -0.06, 4.7, 1.9, 2.3, 2.17000008, 2.06999993, 1.6, 0.69, 1.01, 0.84, 1.2, 1.29, 2.24, 2.35, 4.8, 0.93, 4.6, 1.9, 2.17, 1.22, 0.54, 0.39, 2.0, 0.11, 4.5, -0.14, 1.96000004, 0.76, 4.9, 2.01999998, 1.79999995, 1.5, 0.67, 1.1, -0.24, 2.33999991, 1.45, 1.16, 2.1099999, 0.85, 5.1, 2.3900001, 2.11, 0.12, 0.29, 1.49, 0.5, -0.28, 0.04, 1.9, 3.39, 4.2, 2.0, 0.71, 1.15, 0.9, 2.6, 2.27, 1.98000002, 1.6, 1.3, 1.77999997, 0.99, 0.97, 0.38, 0.28, 0.81, 1.03, 0.64, 0.59, -0.06, 0.11, 2.14, 1.87, 0.39, 1.1, -0.39, 1.3, -0.38, 0.67, 1.3, 4.5, 4.6, 0.77, 0.35, 0.25, 1.9, 2.52, 4.6, 0.86, 0.05, 4.7, 4.4, 1.4, 2.77, 0.85, 1.5, 0.9, 0.46, 0.41, 1.77, 0.65, 1.6, 1.22, 0.87, 5.5, 5.5, 0.76, 1.49, 0.65, 0.36, 4.8, 0.87, 0.08, 1.6, 0.8, 4.4, 1.1, 2.0, 1.32, 0.36, 0.73, 0.85, 1.89, 5.3, 1.73000002, 0.77, 1.75, 0.4, 4.8, 1.28, -0.13, 0.83, 4.3, 0.47, 1.22, 0.29, 0.86, 0.99, 0.73, 0.46, 1.4, 1.95, 0.36, 4.4, 0.58, 0.58, 2.5, 1.32, -0.15, 0.4, 0.58, 1.52, 0.95, 1.75, 4.3, 4.3, 2.8, 0.35, 1.98, 1.6, 2.39, 1.70000005, 0.47, 0.32, 0.48, 1.9, 1.2, 0.87, 1.6, 0.71, 0.84, 0.86, 0.9, 0.94, 1.27, 0.81, 1.1, 2.23, 1.61, 1.79, 1.34, 1.53, 1.03, 0.56, 1.49, 3.81, 0.06, 1.4, 1.8, 0.35, 2.9, 1.5, 1.0, 1.4, 0.92, 0.85, 2.9, 1.6, 2.2, 1.83, 2.5, 1.84, 1.35, 4.2, 0.56, 1.3, 0.7, 1.5, 1.5, 1.87, 1.5, 1.2, 1.0, 1.29, 4.3, 2.1, 1.98, -0.03, 1.17, 0.5, 4.4, 2.27, 1.44, 0.62, -0.16, 1.0, 1.72000003, 1.7, 0.12, 4.6, 1.1, 1.1, 3.2, 1.07, 4.9, 1.54, 1.79999995, -0.75, 1.6, 1.05, 2.35, 0.93, 2.1, 4.2, 0.87, 0.86, 0.45, 4.7, 2.1, 1.28, 0.64, 4.9, 0.51, 0.68, 1.6, 1.36, 0.35, 1.70000005, 4.4, -0.21, 1.21, 0.6, 1.8, 0.72, 0.2, 0.79, 1.53, 2.0, 1.8, 0.63, 0.35, 1.08, 1.2, 2.62, 0.73, 4.0, 1.6, 1.6, 4.2, 1.5, -0.97, 1.74, 0.92, 1.17, 1.65, 0.2, 2.18, 1.74, 0.99, 0.33, 4.6, 0.85, 0.73, 2.24, 1.77, 2.4, 0.75, 1.6, 1.2, 4.1, 2.37, 0.84, 1.7, 2.69, 1.61, 0.1, 2.11, 1.31, 1.0, -0.4, 0.86, 1.47, 1.97000003, 4.4, 1.7, 0.52, 0.19, 4.6, 1.4, 2.1500001, 4.5, -0.08, 0.52, 0.37, -0.42, 1.55, 2.0, -0.01, 1.06, 1.5, 0.65, 2.19, 0.9, 1.0, 1.65, 1.59, 0.73, 2.3, 1.75, 1.3, 4.8, 0.2, 2.00999999, 2.7, 1.79, 2.2, 1.8, 1.6, 1.6, 0.26, 1.2, 0.33, 2.84, 1.9, -0.06, 1.9, 0.75, 1.6, 1.8, 2.2, 1.72, 1.04, 0.86, 1.7, -0.3, 1.1, 1.4, 0.95, 1.83000004, 0.95, 3.4, 4.3, 1.7, 3.9, 2.7, 4.9, 0.84, 0.75, 1.6, 1.3, 2.26, 1.12, 1.6, 1.5, 1.2, 1.1, 2.1, 2.93, 1.6, 0.54, 2.1, 2.04999995, 1.4, 4.4, 2.1, 0.96, 4.6, 2.0, 1.3, 0.78, 1.88, 1.0, 0.99, 0.39, 0.36, 0.46, 0.62, 2.3, 2.9, 0.82, 2.2, 2.9, 1.88, 1.9, 0.75, 1.68, 0.21, 1.5, 0.58, 0.64, 4.3, 0.55, 2.16, 0.37, 1.99000001, 2.0, 1.28, 1.6, 1.1, 0.37, 1.7, 1.5, 1.72, 0.77, 1.46, 2.51, 3.97, 1.67, 0.6, 0.39, 1.9, 1.6, 0.37, 0.9, 1.18, 1.85000002, 1.7, 0.85, 0.97, 5.0, 1.8, 0.88, 3.5, 1.7, 0.6, 2.0, 2.0, 0.73, -0.07, 1.05, 1.7, 1.89, 1.88, 1.25, 4.8, 1.4, 1.84000003, 1.8, 0.8, 1.9, -0.05, 0.8, 2.1, 1.4, 1.19, 4.7, 4.8, 2.24000001, 0.83, 1.7, 0.6, 4.1, 0.73, 1.8, 0.8, 1.1, 1.85, 0.35, 3.4, 2.1, 4.6, 4.0, 0.96, 1.24, 0.45, 4.1, 1.5, 1.64, 0.37, 0.23, 0.03, 0.85, 0.72, 1.9, 2.5, 2.8, 0.35, 4.6, 1.19, 0.6, 4.5, 0.35, 1.13, 2.38, 1.91, 1.4, 1.16, 4.2, 1.67, 2.3, 1.8, 0.35, 4.2, 0.21, 0.8, 4.3, 1.75, 2.27, 2.00999999, 1.5, 1.02, 0.76, 2.42, 2.2, 0.37, 1.64, 0.8, 1.5, 1.82, 1.52, 1.5, 3.13, 1.05, 1.5, 1.7, 4.3, 0.9, 4.3, -0.17, 0.36, 1.72, 1.4, 4.6, 2.77, 1.35, 2.32, 0.88, 1.7, 0.3, 1.1, 5.2, 1.56, 4.2, 1.7, 2.7, 4.7, 0.3, 0.6, 3.21, 0.8, 1.8, 0.44, 1.98, 2.32, 0.68, 3.2, 4.6, 1.48, 1.4, 2.16, 1.16, 0.96, 4.7, 3.25, 0.8, 1.85, 1.1, 1.66, 1.64, 1.38, 1.99000001, 1.58, 1.7, 2.2, 0.59, 0.36, 1.17, 0.76, 1.0, 5.8, 3.32, -1.18, 4.3, 2.04, 0.89, 1.6, 2.39, 1.72, 1.96, -0.31, 1.6, 1.71, 2.9, 2.32, 2.19, 3.8, 1.92999995, 1.54, 1.92999995, 0.45, 0.86, 1.56, 1.74, 0.16, 0.56, 0.94, 0.61, 1.23, 0.43, 1.3, 4.6, 1.09, 4.5, 1.2, 0.99, 1.7, 0.8, 0.38, 4.4, 0.21, 4.4, 0.77, 2.11999989, 1.19, 1.78, 1.2, 0.5, 5.0, 1.32, 0.78, 1.79, 2.2, 0.9, 2.33, -0.12, 1.06, 1.45, 1.5, 2.6, 1.9, 2.04, 1.91999996, 0.8, 1.31, 1.9, 1.4, 1.15, 2.35, 1.6, 1.44, 3.1, 0.65, 2.12, 2.3, 1.91, 4.2, 2.41, 2.5, 1.85, 3.9, 1.5, 1.58, 1.5, 0.37, 0.86, 1.28, 0.63, 1.51, 4.2, 1.29, 2.08, 0.88, 1.8, 0.45, 0.7, 1.19, 0.48, 2.32, 2.37, 1.5, 1.3, 2.16, 2.09, 1.6, 0.88, 1.4, 0.1, 1.93, 1.9, 1.58, -0.03, 1.94, 1.45, 0.4, 0.48, 0.92, 1.19, 1.1, 3.41, 2.42, 0.9, 3.13, 1.76, 0.4, 2.75, 1.4, 1.66, 4.3, 2.4, 1.96, 4.6, -0.35, 0.73, 1.47, 0.85, 1.97, 1.44, 1.4, 2.86, 0.85, 5.1, 1.29, 0.89, 1.7, 0.09, 0.45, 1.5, 1.4, 0.75, 1.2, 2.18, 1.67, 2.05, 3.1, 0.49, 1.3, 0.74, 0.64, 1.84000003, 0.39, 2.7, 0.6, 1.4, 1.07, 2.7, 0.97, 1.4, 3.8, -0.21, 3.9, 1.4, 1.1, 1.54, 0.01, 0.06, 0.64, 1.7, 0.7, 0.46, 4.2, 2.33999991, 0.6, 1.5, 1.22, 1.8, 1.0, 1.74, 0.31, -0.05, 1.32, 1.3, 0.93, 1.89, 1.5, 1.3, 1.1, 1.0, 1.1, 4.1, 1.4, 2.0999999, 1.5, 0.22, 0.84, 2.2, 1.86, 2.1, 2.1, 2.0, 1.4, 2.38, 1.3, 0.56, 5.0, 0.55, 4.7, 1.5, -0.62, 2.6, 0.98, 2.8, 1.02, 1.6, 0.85, 1.0, 0.45, 3.27, 2.4, 1.5, 0.37, 1.76, 2.3, 0.58, 4.2, 4.6, 1.99000001, 0.81, 2.82, 1.6, 0.64, 1.52, 0.47, 0.86, 1.9, 4.4, 4.3, 1.6, 0.85, 2.26, 4.5, 0.35, 2.05, 4.1, 1.7, 4.6, 1.15, 0.84, 4.4, 2.43, 1.6, 0.6, 0.57, 4.6, 2.7, 1.1, 1.4, 1.2, 2.64, 4.5, 2.38, 1.3, 1.1, 4.5, 2.2, 0.88, 1.59, 1.0, 0.94, 0.66, -0.53, 1.9, 0.86, 1.3, 1.38, 0.73, 4.9, 1.1, 0.85, 2.98, 3.21, 0.17, 2.2, 0.99, 0.42, 1.72000003, 0.77, 1.6, 2.24, 1.15, 1.23, 0.86, 0.4, 2.04, -0.66, 3.1, 0.56, 1.88, 0.4, 1.4, 0.96, 0.24, 0.82, 0.85, 0.94, 0.88, 0.53, 0.38, 0.85, 2.1, 1.1, 2.0, 1.5, 0.62, 1.8, 2.1, 0.57, 1.7, 1.22, 1.85, 3.8, 2.3, 1.06, 0.44, 1.83, 5.0, 4.6, 0.84, 4.3, 0.71, 1.7, 1.02, 1.58, 1.29, 0.86, 1.18, 1.67, 1.3, 0.71, 0.85, 1.16, 2.06, 0.8, 2.1400001, 0.85, -0.06, 2.4, 1.4, 0.34, 1.5, 0.98, 1.39, 3.3, 1.64, 2.8, 3.26, 1.49, 4.1, 2.1, 0.96, 6.0, 1.3, 4.1, 0.8, 1.06, 1.61, 0.9, -0.08, 2.27, 0.7, 2.1, 0.78, 4.6, 0.66, 0.81, 2.0999999, 0.89, 1.98, 4.1, 4.8, 0.85, 1.38, 6.6, 0.76, 0.4, 4.6, 0.91, 0.84, 0.1, 0.19, 3.0, 0.71, 0.88, 4.7, 2.6, 1.68, 0.85, 2.4, 0.61, 2.36, 0.47, 0.81, 1.2, 1.07, 0.71, 0.48, 1.19, 2.1, 2.17, 1.6, 0.9, 1.72000003, 4.5, 2.45, 0.28, 0.81, 1.7, 1.7, 1.0, 1.0, 1.5, 1.2, 0.55, 0.98, 2.16, 4.5, 2.3, 1.71, 1.17, 4.4, 1.18, 0.76, 1.3, 5.1, 4.5, 0.38, 2.2, 1.6, 0.91, 1.12, 0.84, 1.4, 0.63, 1.51, 4.8, 4.9, 4.8, 1.6, 2.07999992, 1.55, 2.1, 0.37, 2.1, 0.85, 0.01, 3.15, 1.5, 4.3, 1.45, 2.1, 1.5, 1.6, 1.76, 1.82000005, 1.19, 1.4, 4.2, 1.5, 0.54, 4.5, -0.79, 1.79, 0.98, 1.9, 4.3, 1.7, 1.6, 1.85000002, 1.7, 1.85, 1.41, 0.77, 2.21, 0.3, 1.69, 1.9, 4.1, 0.26, 0.8, 2.33999991, 2.07999992, 2.04, 4.3, 0.85, 0.5, 0.6, 1.84000003, 2.4, 0.09, 2.4, 1.68, 1.2, 0.64, 0.36, 2.3, 0.72, 1.03, 1.74, 4.5, 1.71000004, 1.59, 2.4, 1.8, 1.91, 0.46, 0.2, 2.1, 0.72, 1.4, 4.4, 1.6, 1.1, 1.6, 0.49, 1.56, 4.4, 2.2, 1.38, 2.1, 0.59, 2.81, 5.1, 1.0, 1.67, 1.02, 1.5, 0.64, 2.22, 2.2, 1.7, 1.38, 1.82, 4.1, 2.5, 0.25, 2.18, 1.89, 1.1, 4.6, 1.1, 0.81, -0.04, 0.84, 0.49, 1.7, 0.76, 1.52, 1.0, 1.16, 1.13, 0.85, 0.83, 4.3, 1.6, 1.3, -0.2, 2.29, 1.3, 0.2, 2.1, 0.52, 1.5, 2.12, 1.54, 0.35, 0.21, 1.3, 1.9, 1.3, 1.4, 4.6, 1.21, 2.3, 1.66, -0.13, -0.51, -0.6, 3.0, -0.54, 0.71, 1.6, 1.7, 1.51, 0.85, 2.36, 0.96, 1.75, 0.91, 1.1, 1.0, 0.36, 0.85, 4.6, 2.33, 1.63, 1.6, 1.83000004, 1.56, 0.84, 2.94, 1.25, 2.1, 2.57, 1.6, 0.49, 1.41, 1.49, 0.9, 2.4000001, 1.39, 0.72, 1.1, 2.82, 1.66, -0.62, 2.2, 2.03999996, 1.3, 1.64, 0.72, 1.83, 1.1, 0.17, 2.47000003, 0.4, 1.94, 1.46, 1.99, 1.7, 1.59, 1.2, 1.8, 1.54, 1.26, 0.31, 1.3, 4.8, 2.4, 1.0, 2.32, 2.09, 1.75, 2.3, 1.3, 0.87, 1.16, 1.71, 2.22, 1.39, 1.79, 0.86, 2.54, 0.36, 0.34, 1.51, 2.28, 1.9, 2.1, 1.1, 0.74, 4.4, 1.3, 0.92, 4.3, 2.42, 0.64, 2.05999994, 1.83000004, 0.35, 2.13, 1.31, 4.0, 1.1, 0.85, 1.16, 0.45, 0.85, 0.8, 4.4, 1.6, 0.38, 1.8, 2.5, 4.5, 2.1, 2.62, 2.7, 1.12, 3.9, 2.8, 0.86, 4.1, 0.76, 1.9, 1.35, 0.46, 1.16, 1.51, 1.21, 0.84, 3.0, 2.76, 0.79, 1.15, 0.7, 1.2, 2.1, 2.11, 4.8, 4.1, 0.68, 1.06, 4.5, 0.68, 1.35, 1.9, 2.7, 1.4, 2.1, 1.8, 2.7, 1.86000001, 0.82, 1.7, 4.4, 0.29, 1.7, 1.6, 2.5, 1.63, 1.27, 1.3, 0.31, 1.70000005, 4.2, 1.9, 0.59, 0.48, 1.3, 1.8, 2.5, 0.8, 0.45, 0.76, 0.23, 2.8, 1.6, 0.84, 0.8, 0.87, 0.61, 2.35, 1.15, 4.3, 2.11999989, 1.75, 1.28, 1.84000003, 1.73000002, 1.9, 1.3, 1.83000004, 1.6, 1.01, 1.0, 4.7, 4.6, 1.8, 1.4, 1.9, 2.17, 2.8, 1.1, 3.04, 2.37, 6.2, 5.7, 1.6, 0.4, 0.9, 3.3, 1.0, 1.7, 0.6, 2.1, 1.98, 1.55, 1.77, 3.9, 1.3, 4.5, 1.2, 1.18, 1.02, -0.1, 0.0, 4.3, 2.4, 2.04999995, 0.83, 1.2, 1.73, 2.34, 4.2, 1.8, 0.97, 1.2, 0.58, 4.1, -0.55, -0.01, 1.07, 3.0, 1.1, 2.0, 4.3, 1.3, 5.9, -0.22, 2.25, 2.37, 1.1, 4.6, 1.84, 4.8, 1.2, 1.01, 0.22, 0.79, 2.2, 0.43, 4.2, 0.83, 3.4, 0.2, 1.51, 1.15, 1.18, 1.4, 1.4, 1.6, 2.21, 4.2, -0.23, 0.88, 4.5, 2.3, 1.07, 2.4, 1.8, 1.5, 0.36, 1.9, 2.3, 1.65, 0.85, 0.87, 1.9, 2.18, 3.23, 0.84, 0.17, 4.7, 0.89, 0.4, 2.1500001, 1.1, 1.1, 1.2, 2.1, 1.9, 1.04, 1.2, 0.84, 1.0, 2.59, 1.5, 3.05, 1.5, 0.88, 0.3, 0.64, 1.9, 1.52, 1.0, 0.6, 2.01, 0.9, 1.7, 2.2, 2.1400001, 2.1, 1.4, 1.92999995, 1.8, 2.22, 0.88, 0.7, 1.1, 2.1, 2.13, 1.92999995, 3.0, -0.15, 1.68, 1.88, 1.82000005, 1.3, 2.39, 1.2, 1.18, 0.9, 1.24, 1.4, 0.7, 1.8, 0.47, 1.44, 2.1, 1.1, 4.1, 1.72, 1.6, 2.5, 1.58, 1.6, 1.83, 1.63, 4.3, 2.0, 1.7, 0.14, 1.56, 1.02, 1.3, 4.7, 1.53, 0.85, 0.08, -1.17, -0.52, 4.4, 1.6, 1.1, 3.03, 1.3, 1.7, 1.6, 1.2, 0.37, 1.52, 1.8, 1.1, 0.53, 2.7, 2.2, 3.65, 1.4, 1.6, 0.76, 2.5, 1.4, 1.7, 1.61, 4.2, 0.47, 4.5, 4.5, 1.8, 1.67, 5.1, 0.9, 0.33, 1.3, 0.6, 1.0, 0.86, 1.82, 0.58, 1.1, 5.0, 4.6, 0.49, 0.9, 2.24000001, 2.6, 0.7, 0.84, 2.0, 4.5, 0.5, 1.2, 0.85, 1.3, 2.0, 0.21, 2.9, 4.1, 2.7, 1.69, 1.83, 4.7, 4.4, 0.82, 0.6, 0.8, 4.5, 2.5, 1.5, 1.3, 0.7, 1.1, 1.2, 1.57, 2.0, 1.75999999, 1.89, 1.7, 1.65, 1.8, 1.6, 1.5, 1.9, 1.1, 1.1, 1.3, -0.56, 1.7, 1.2, 1.16, 1.4, 1.7, 1.1, 1.18, 1.7, 2.2, 2.0, 1.5, 1.6, 1.3, 1.7, 1.7, 1.6, 2.3, 4.6, 0.64, 1.2, 1.7, 4.2, 1.2, 0.09, 0.35, 4.4, 3.2, 1.4, 0.36, 0.13, 1.6, 2.1, 2.68, 1.01, 0.84, 2.0, 1.6, 4.1, 2.2, 1.3, 1.2, 1.3, 0.8, 0.7, 0.7, 1.4, 1.08, 0.4, -0.2, 0.18, 1.08, 0.65, 2.19, 0.9, 2.7, 2.0, 1.12, 1.52, 1.09, 1.84000003, 0.28, 0.56, 4.3, 1.3, 0.7, 1.4, 2.17000008, 1.9, 2.0, 0.55, 2.1, 1.1, 2.5, 1.6, 2.68, 1.54, 1.3, 1.8, 3.6, 2.66, 0.74, 0.85, 0.62, 4.2, 1.6, 2.2, 1.46, 0.84, 1.9, 2.08999991, 1.7, 2.4, 1.0, 1.2, 1.1, 0.9, 0.95, 1.96000004, 1.76999998, 2.22, 1.6, 0.87, 1.1, 1.02, 0.8, 0.8, 1.2, 2.5, 1.1, 1.0, 2.7, 0.6, 2.9, 2.01, 0.6, 1.1, 0.53, 0.66, 1.19, 1.15, 1.2, 2.0, 1.9, 1.8, 0.8, 2.8, 4.2, 1.2, 1.1, 0.28, 0.47, 1.1, 1.2, 0.6, 0.4, 1.4, 2.9, 1.65, 2.2, 2.42, 2.95, 1.6, 2.1, 1.96, 0.5, 2.06, 0.4, -0.04, 0.5, 1.3, 2.0, 1.02, 2.1500001, 0.39, 4.8, 1.6, 0.8, 1.0, 2.5, 1.15, 0.2, 0.03, 0.22, 0.7, 1.6, 2.06, 1.2, 0.67, 2.2, 1.99000001, 2.0, 2.6, 4.6, 0.25, 0.9, 1.94000006, 2.1, 2.4, 2.99, 1.0, 0.74, 1.83, 1.6, 0.84, 3.2, 1.23, 1.3, 0.37, 0.22, 0.9, 5.0, 2.0, 0.54, 1.9, 0.8, 0.9, 4.6, 2.5, 0.47, 2.3, 2.08999991, -0.09, 1.24, 1.7, 4.2, 0.55, 4.2, 4.8, 2.14, 4.6, 1.8, 1.4, 0.49, 2.2, -0.41, 1.74, 2.3, 0.6, 0.7, 1.5, 0.0, 1.1, 4.2, 2.17, -0.46, 1.3, -0.08, 0.4, 1.1, 2.7, 1.1, 0.7, 1.64, 0.7, 0.2, 1.6, 1.6, 4.5, 1.37, 0.63, 0.7, 1.7, 1.94000006, -0.4, 1.6, 1.37, 1.8, 0.87, 4.4, 0.86, 0.12, 1.1, 1.6, 0.36, 0.85, 2.4, 0.8, 0.8, 0.85, 2.22, -0.91, 1.83000004, 3.1, 0.5, 1.83, 2.4, 1.1, 0.8, -0.43, 2.11, 1.1, 1.8, 0.85, 0.7, 1.2, 1.94, 1.90999997, 2.73, 2.35, 0.85, 1.37, 0.57, 1.9, 1.5, 2.01, 0.47, 1.6, 1.0, 0.27, 1.4, 1.24, 0.52, 1.2, 1.6, 1.27, 0.46, 1.22, 0.89, 0.86, 1.3, 2.79, 2.0, -0.46, 0.57, 0.45, 0.92, 0.6, 0.63, 2.81, 4.5, 1.6, 1.2, 0.9, 4.5, 0.85, 1.3, 2.39, 0.68, 2.52, 5.1, 2.72, 1.65, 1.7, 1.88, 0.58, 1.02, 4.4, 1.86, 1.5, 4.4, 4.4, 3.5, 1.3, 0.85, 0.86, 1.7, 1.47, 0.7, 0.53, 0.13, 4.3, 1.65, 1.69, 0.03, 1.28, 2.02999997, 0.29, 1.3, 4.7, 4.6, 0.55, 1.4, 0.06, 0.59, 0.75, 1.62, 0.47, 2.1, 2.0, 2.0, 0.79, 0.89, 4.1, 1.04, 1.73000002, 1.3, 0.87, 0.85, 2.09, 2.32, 2.32, 1.6, 1.65, 1.5, 1.89999998, 1.57, 0.8, 1.74, 0.38, 0.0, 1.6, 1.36, 1.3, 0.95, 0.35, 1.34, 0.71, 1.97, 0.92, 1.1, 1.18, 0.43, 0.8, 2.2, 4.4, 0.21, 4.5, 2.13, 0.84, 2.41, 2.0, 1.2, 2.14, 0.7, 0.96, 2.0, 1.5, 1.72, 1.5, 2.1, 1.11, 1.7, 4.2, 1.9, 0.33, 0.56, 0.61, 4.4, 1.69, 1.62, 1.59, 1.2, 1.7, 0.85, 0.35, 1.69, 1.61, 1.38, 0.56, 1.8, 3.57, 1.27, 1.49, 0.7, 1.9, 1.9, 1.5, 2.34, 2.96, 0.35, 1.44, 1.6, 2.81, 0.9, 1.7, 3.24, 1.4, 1.83, 0.93, 0.75, 0.17, 1.55, 2.0, 1.6, 1.17, 0.72, 2.1500001, 1.38, 0.8, 2.64, -0.43, 0.99, 3.31, 0.84, 0.8, 1.68, 1.1, 0.63, 1.06, 1.3, 1.58, 1.9, 0.84, 1.6, 2.37, 0.42, -0.13, -0.02, 1.31, 1.8, 1.0, 1.1, 1.42, 2.38, 0.84, 2.23, 3.4, 1.06, 0.07, 1.78999996, 2.23, 0.91, 1.3, 1.4, 1.9, 4.4, 4.2, 0.9, 1.3, 1.46, 0.89, 1.22, 1.12, 4.3, -0.08, 1.7, 2.35, 1.2, 1.2, 1.11, 2.02999997, 4.5, 2.42, 1.86000001, 1.73, 5.4, 1.05, 0.35, 1.2, 1.54, 5.2, 0.91, 1.4, 1.33, 1.28, 1.15, 1.19, 0.37, 1.8, 0.9, 1.15, 0.88, 1.08, 0.83, 1.05, 0.51, 2.1, 2.29, 0.6, 1.01, 1.3, 1.13, 0.93, 1.88, -0.19, 2.5, 1.16, 0.97, 1.51, 1.25, 1.4, 0.04, 1.75, 0.65, 1.45, 1.8, 4.0, 2.8, 1.1, 4.3, 4.4, 1.2, 4.3, 1.8, 0.69, 1.6, 1.56, 1.1, 0.55, 1.5, 1.09, 0.9, 1.08, 1.88, 1.3, 1.1, 4.7, 1.6, 0.79, 2.0, 4.4, 1.6, 2.7, 4.7, 4.1, 1.8, 1.2, -0.63, 2.25, 4.0, 1.2, -0.16, 1.5, 0.38, 4.5, 0.15, 0.79, 4.4, 1.87, 2.1400001, 0.68, 2.11, 4.8, 2.4, 1.6, 0.04, 0.86, 1.49, 0.1, 0.8, 0.38, 1.5, 0.65, 3.36, 1.4, 1.1, 1.05, 1.5, 1.99, 1.6, 0.83, 0.71, 4.7, 0.45, 0.89, 0.98, 0.34, 1.89, 0.95, 0.84, 0.93, 1.76, 2.86, 1.47, 1.3, 4.3, 1.8, 4.7, 2.2, -0.03, 2.52, 1.82, 2.15, 1.7, 0.72, 1.4, 0.46, 1.84, 5.3, -0.95, 1.5, 1.5, 0.52, 2.3, 1.8, 2.5, 2.1, 0.3, 0.85, 1.3, 0.02, -0.01, -0.42, 6.0, 0.84, 1.1, 0.8, 1.21, 1.61, 0.92, 0.9, 1.1, 1.14, 0.73, -0.33, -0.12, 0.42, 0.33, 1.39, -0.16, 2.0, 1.74, 4.4, 5.3, 1.18, 2.04, 1.96, 2.23000002, 0.47, 1.56, -0.02, 1.62, 0.37, 0.73, 1.68, 0.29, 0.38, 0.81, 1.94, 1.1, 2.5, 0.5, 0.86, 0.54, 0.38, 1.45, 0.67, 1.3, 1.02, 1.3, 1.9, 0.9, 2.03, 1.8, 2.3, 0.0, 1.7, 0.04, 4.6, 0.84, 4.7, 0.6, 0.41, 1.12, 1.1, 1.49, 1.19, 4.5, 2.9, 1.88999999, 0.85, 1.97000003, 0.46, 0.46, 1.77, 2.0, 1.86, 2.3, 1.5, 4.4, 1.3, 2.63, 1.1, 0.32, 2.03999996, 0.35, 1.42, 0.85, 0.44, 2.29, 0.33, 2.98, 0.5, 0.27, 0.15, 0.2, 1.4, 2.3, 0.24, 4.1, 1.6, 1.4, 2.36, 1.21, 0.78, 0.5, -0.38, 1.86000001, 4.3, 1.8, 1.13, 0.05, 4.7, 2.5, 0.37, 0.21, 0.85, 2.6, 1.9, 0.21, 1.71, 4.2, 4.5, 1.5, 0.6, -0.96, 0.67, 1.97000003, 0.0, 3.08, 1.5, 1.13, 4.3, 0.49, 0.05, 0.8, 1.2, 1.2, 2.44, 1.3, 0.02, 2.66, 0.65, 1.02, 1.13, 5.1, 1.93, 1.82, 1.5, 0.36, 0.85, 2.06, 1.88, 1.65, 2.24, 0.39, -0.22, 0.95, -0.04, 0.8, 4.3, 0.23, 1.06, 1.27, 4.2, 1.2, 1.4, 1.1, 1.5, 1.2, 1.12, 1.9, -0.24, 2.64, 1.8, 1.6, 0.76, 1.2, 0.87, 1.1, 1.83000004, 4.2, 1.57, 0.93, 2.7, 1.95000005, 0.74, 1.86000001, 0.8, 2.32999992, 1.3, 4.3, 1.0, 0.6, 2.4, 2.46, 2.5, 1.18, 2.4, 1.42, -0.5, 0.02, 0.9, 1.74000001, 5.1, 1.3, 3.07, 1.4, 2.83, 1.2, 4.3, 1.0, 0.3, 1.1, 1.3, 1.3, 0.41, 1.19, 2.00999999, 2.2, 1.38, 4.0, 3.4, 1.79, 0.69, 1.7, 0.69, 4.5, 0.48, 0.85, 1.25, 1.22, 2.9, 1.35, 1.9, 1.77, 1.33, 4.1, 1.36, 0.62, 1.6, 1.6, 0.94, 0.78, 1.99000001, 1.89, 1.47, 4.6, 0.81, 0.37, -0.66, 0.08, -0.93, 1.64, 1.42, 1.03, 0.5, 1.1, 0.72, 1.29, 2.9, 1.01, 1.68, 1.2, 0.44, 1.07, 4.5, 1.6, 3.07, 1.39, 1.6, 0.37, 0.95, 0.86, 1.2, 2.1, 0.23, 0.23, 1.53, 1.31, 1.56, 1.53, 0.65, 1.13, 0.81, 1.76, 2.73, 2.37, 2.2, 0.6, 2.27999997, 1.38, 1.9, 0.57, 0.27, 1.82, 1.42, 1.1, -0.6, 1.3, 1.32, 1.5, 1.7, 2.12, 0.9, 0.85, 0.67, -0.04, 0.99, 1.4, 3.06, 1.2, 0.34, 2.25999999, 0.87, 2.42, 0.41, 0.51, 1.8, 1.1, 4.8, 0.84, 0.67, 0.5, 0.56, 1.5, 0.76, 0.98, 1.4, 0.6, 0.4, 0.21, 2.1, 1.61, 4.9, 4.5, 1.1, 1.04, 0.85, 1.4, -0.35, 0.85, 3.5, 4.1, 1.17, 0.9, 0.4, 0.64, 1.2, 0.8, 1.1, 4.5, 1.95, 0.59, 0.1, 1.77, 4.6, 1.2, 3.36, 2.01, 1.2, 0.48, 1.11, 1.45, 1.6, 0.16, 4.3, 0.8, 2.42, 0.22, 0.64, 2.38, 1.0, 2.5, 1.4, 1.1, 1.5, 1.19, 0.5, 4.3, -0.14, 1.45, 1.74, 1.15, 1.1, 1.99000001, 2.28, 0.69, 2.56, 3.3, 0.9, 1.26, 3.19, 2.2, 0.85, 1.0, 1.02, 1.1, 1.17, 1.91999996, 1.56, 0.0, 0.68, 2.8, 0.98, 0.85, 0.84, 2.2, 0.85, 2.9, 0.03, 1.44, 0.89, 1.23, 0.85, 0.72, 0.94, 0.85, 1.17, 1.6, 0.85, 1.31, 0.09, 2.1, 0.81, 0.69, 1.12, 1.19, 1.1, 1.1, 0.85, 0.84, 4.2, 2.79, 1.13, 0.44, 1.09, -0.04, 2.0, 0.56, 1.4, 1.18, 0.97, -0.04, 2.64, 1.65, 1.42, 1.15, 1.26, 1.95, 0.58, -0.2, 0.52, 0.68, 1.91, 1.4, 1.9, 2.39, 0.4, 0.35, 0.35, 0.84, 4.6, 0.57, 1.7, 4.9, 2.65, 3.18, 0.9, 1.4, 2.97, 1.4, 2.1, 0.1, 1.6, 4.5, 0.4, 1.7, 0.85, 2.2, 1.6, 2.0, 1.4, -0.09, 0.9, 2.25999999, 1.4, 2.31, 0.1, 1.17, 2.5, 1.46, 1.67, 3.0, 1.56, 1.24, 1.64, 1.7, 0.94, 4.2, 2.8, -0.15, 1.0, 5.0, 0.9, 1.45, 3.34, 0.9, 1.4, 0.85, 4.5, 0.9, 2.79, 1.4, 1.74, 1.63, 0.21, 2.14, 2.28, 1.2, 1.02, 2.8, 0.28, 0.98, 0.73, 0.9, 2.1400001, 1.46, 2.3, 1.37, 2.00999999, 3.3, 1.79, 0.66, 2.01999998, 0.54, 1.2, 0.86, 0.75, 2.76, 0.96, 0.98, 0.24, 1.21, 2.1, 1.3, 2.49, 1.25, 1.56, 0.91, 2.5, 0.95, 0.86, 1.7, 2.2, 0.69, 0.5, 1.6, 0.6, -0.03, 4.1, 1.02, 1.6, 2.67, 1.2, 1.54, 1.03, 1.33, 1.41, 2.34, 2.18, 1.53, 0.6, 1.26, 1.72, 1.3, 1.58, 2.7, 5.1, 3.9, 1.1, 2.29, 1.98000002, 1.68, 1.22, 0.58, 1.7, 0.1, 1.43, 0.5, 1.67, 0.86, 1.18, 0.02, 0.36, 2.7, 0.55, 1.7, 1.4, 4.3, 1.85000002, 1.54, 2.1, 1.3, 0.72, 5.5, 1.5, 1.6, 5.2, 0.27, 1.94, 0.44, 5.3, 4.4, 1.35, 1.0, 0.86, 0.9, 1.3, 0.46, 1.2, 1.95, 4.2, 0.59, 1.5, 4.5, 2.57, 0.67, 0.29, 1.3, 0.61, 1.34, 0.9, 2.43, 4.5, 2.28, 1.95000005, 1.6, 2.3, 3.1, 2.27999997, 1.31, 1.89, 0.46, 1.11, 2.2, -0.57, 1.1, 0.6, -0.57, 0.32, 1.7, 4.2, 1.94, 1.7, 0.96, 1.59, 2.3, 1.5, 4.4, 1.96000004, 1.8, 1.3, 1.9, 1.23, 4.9, 2.3, 0.8, 1.54, 2.76, 2.72, 1.5, 1.0, 1.52, 0.45, 5.2, 1.14, 4.9, 2.89, 1.0, 0.7, 2.29999995, 2.36, 4.5, 0.14, 1.6, 1.97000003, 0.63, 1.2, 1.6, 1.5, 2.19, 2.29, 3.5, 1.5, 1.0, 2.4, 1.8, 2.9, 1.77, 4.4, 4.2, 2.5, 1.4, 2.04, 4.2, 1.46, 0.64, 4.4, 1.55, 0.6, 0.95, 0.99, 1.4, 2.26, 1.33, 1.4, 4.8, 0.89, 4.2, 1.8, 2.1400001, 1.6, 1.48, 1.49, 2.69, 4.0, 4.4, 0.4, 1.35, 2.3, 1.71, 1.26, 2.7, 5.7, 0.41, 1.87, 4.8, 4.5, 1.3, 1.99000001, 1.75, 1.5, 0.6, 2.04, 1.21, 2.4, 1.28, 4.3, 0.0, 2.35, -0.5, 1.76, 4.2, 3.3, 0.24, 1.7, 0.87, 1.62, 1.4, 0.5, 0.5, 1.08, 0.56, 4.08, 2.39, 1.03, 1.37, -0.06, 0.89, 1.74, 0.82, 0.65, 1.56, 2.18000007, 1.83, 1.89, 2.13000011, 1.52, 4.2, 1.89999998, 1.8, 1.31, 1.17, 1.69, 4.2, 4.2, 0.06, 2.03, 1.3, 1.42, 0.9, 1.11, 1.8, 0.91, 1.53, 1.1, 0.45, 1.02, 1.98, 2.9, 1.48, 1.0, 1.13, 1.1, 1.08, 2.41, 1.8, 0.85, 1.8, 1.17, 2.15, 0.33, 4.6, 1.7, 2.8, 1.8, -0.2, 0.96, 2.3, 1.65, 0.95, 1.4, 2.82, 0.53, 1.67, 0.85, 0.86, 1.89, 0.94, 1.15, 4.2, 0.67, -0.41, 0.13, 1.3, 2.3, 0.93, 1.5, 0.6, 0.16, 1.16, 0.37, 4.1, 1.73, 0.9, 1.19, 0.8, 0.56, 1.82, 4.3, 0.97, 1.3, 0.7, 1.45, 4.4, 1.4, 0.17, 1.7, 0.9, 2.2, 1.73, 1.4, 1.6, 1.48, 4.0, 4.5, 0.55, 4.3, 1.01, 1.17, 1.89, 2.5, 2.4, 1.73000002, 0.76, 2.6, 4.2, 1.4, 1.88, -0.32, 0.77, 0.9, 2.00999999, 1.5, 0.96, 0.41, 0.25, 4.5, 4.8, 1.12, 1.9, 0.16, 1.07, 3.0, 1.72, 0.62, 0.66, 1.6, 1.8, 1.07, 3.7, 1.08, 1.2, 1.94, 0.85, 5.0, 1.21, 0.35, 1.5, 1.09, 0.42, 4.8, 2.7, 0.55, 1.5, 4.5, 0.7, 4.3, 1.53, 0.92, 2.0, 0.7, 0.23, 0.78, 0.01, 1.82000005, 1.8, 1.91999996, 0.99, 0.46, 0.61, 0.85, 1.52, 0.85, 1.99, 1.52, 2.1, 0.38, 1.63, 1.23, 1.48, 0.91, 1.8, 2.0, 1.44, 2.7, 0.78, 1.89999998, 1.6, 1.9, 0.85, 1.27, 0.37, 1.03, 1.7, 1.89, 0.1, 1.6, 1.12, 1.06, 1.16, 1.2, 0.44, 1.16, 2.1, 0.53, 4.5, -0.18, 0.58, 0.56, 0.37, 0.32, -0.48, 3.9, 0.78, 1.6, 1.71, 4.0, 1.22, 0.44, 0.36, 1.9, 3.1, 0.72, 1.8, 4.9, 1.5, 1.86, 4.9, 1.34, 1.9, 0.86, 0.2, 0.68, 1.06, 2.5, 1.85, 1.5, 1.09, 0.57, 0.75, 0.01, 1.7, 0.89, 0.54, 0.84, 2.41, 1.44, 1.4, 2.08, 0.7, 0.8, 4.7, 1.17, 1.55, 1.19, 1.73, 1.21, 2.0, 0.49, 0.51, 2.1099999, 2.24000001, 2.54, 1.89999998, 1.8, 1.4, 4.7, 1.5, 4.2, 1.82000005, 2.16, 1.79, 0.94, 2.11, 4.9, 2.2, 0.68, 2.39, 4.3, 0.14, -0.4, 1.67, 1.6, 4.4, 0.6, 1.61, 0.37, 1.81, 0.9, 1.0, 1.64, 1.86000001, 5.7, 5.7, 2.0, 1.78, 0.54, 1.1, 3.37, 1.7, -0.07, 1.2, 2.0, 0.92, 2.2, 4.6, 1.8, 0.94, 0.05, -0.05, -0.35, 1.7, 1.84000003, -0.99, 2.84, 1.01, 4.4, 2.0, 2.1400001, 1.41, 4.2, 4.2, 3.05, 4.7, 1.7, 1.89, 1.5, 0.72, 4.8, 2.56, 4.4, 2.1, 1.93, 0.86, 2.47, 5.1, -0.07, 1.7, 2.48, 2.63, 4.3, 2.32, 4.38, 1.0, 0.84, 1.7, 1.37, 0.81, -0.82, 1.91, 4.5, 1.5, 0.7, 2.0999999, 1.23, 2.13, 0.53, 2.6, 1.0, 0.22, 1.37, 3.9, 4.3, 1.8, 1.9, 1.21, -0.37, 1.9, 0.1, 4.2, 2.46, 0.83, 2.0, 0.36, 0.47, 1.42, 0.82, 1.4, 5.5, 1.44, 1.5, 2.47, 0.99, 1.7, -0.18, 2.03, 1.13, 1.84000003, -0.91, 1.89, 1.7, -0.28, 2.09, 1.9, 1.0, 1.1, -0.6, -1.03, 4.4, 2.28999996, 1.44, 1.62, 2.30999994, -0.17, 2.04, 0.21, 1.1, 0.84, 2.0, -0.98, 1.3, 2.3499999, 1.49, 1.17, 1.51, 2.1, 1.6, 1.44, 1.58, 0.19, 1.85, 0.46, -0.1, 1.52, 1.6, 1.5, -1.01, 0.87, 1.61, 1.5, 1.15, 1.98000002, 1.72, 2.11, 0.66, -0.99, 1.35, 0.87, 0.21, 1.94, -1.03, 0.89, 0.03, 0.67, 3.32, 5.4, 1.70000005, 0.72, 1.3, 5.9, -0.52, 1.08, 4.7, 0.39, 2.52, -0.22, -0.53, 2.1, 1.2, 1.76999998, 0.7, 2.05999994, 1.65, 2.03999996, 0.68, -0.49, -0.71, 1.7, 2.1, 2.2, 2.12, 1.64, 4.3, 2.45, 2.16000009, 1.5, 1.99, 4.6, 4.5, 2.05999994, 2.4, 4.7, 4.9, 1.82, 4.9, 1.49, 1.18, 4.5, 0.7, 1.22, 4.5, 0.81, 1.1, 0.5, 2.8, 0.8, -0.58, 1.63, 0.37, 4.9, 0.64, 1.54, 1.44, 1.72, 0.6, 4.8, 1.7, 0.59, 2.43000007, 4.9, 2.26, 0.96, 0.14, 2.0, 1.8, 0.5, -0.1, 3.8, 0.85, 0.73, 0.7, 3.24, 1.51, 2.0, 1.81, -0.37, 2.0, -0.32, 0.17, 2.06999993, 1.9, 1.7, 1.4, 2.17000008, 0.75, 1.82, 1.52, 1.69, 1.53, 0.95, 0.85, 2.4, 1.92, -0.27, 1.52, 2.1, 1.5, 2.3, 0.37, 2.29, 2.03999996, 1.0, 0.85, 1.83, 4.3, 0.55, -0.01, 2.07, 1.15, 1.9, 4.7, 1.0, 0.14, 1.6, 0.69, 0.93, 2.0, -0.75, 4.1, 2.2, 1.85000002, 3.41, 0.82, 1.04, 1.8, 1.25, 2.1400001, 3.38, 5.0, 0.39, 1.84000003, 4.6, 1.38, 0.86, 0.34, 0.93, 1.45, 4.5, 0.64, 0.52, 1.11, 1.54, 2.36, 3.55, 0.7, 1.8, 1.22, 0.06, 1.59, 2.3900001, 1.78, 0.77, 0.86, 1.58, -0.07, 2.47, 0.6, 1.53, 0.01, 1.1, 0.72, 2.15, 2.12, 0.01, 4.5, 2.02999997, 2.21, 4.0, 2.07, 1.01, 2.7, 5.1, 1.45, 0.07, 0.16, -0.05, 1.82, 1.9, 0.86, 4.2, 1.48, -0.22, 1.67, 5.0, 2.1400001, 2.02, 4.6, 4.6, 4.7, 2.25, 1.5, 2.02999997, 1.77, 1.1, 4.1, 2.2, 2.29, 1.51, 4.4, 0.72, 0.86, 0.69, 1.27, 0.86, 4.6, 4.7, 2.7, 5.3, 0.84, 1.2, 4.6, 0.8, 2.98, 1.22, 1.3, 2.3, 4.1, 4.4, 2.4, 1.9, 4.1, 1.1, 4.4, 1.37, 0.62, 0.95, 1.70000005, 2.0, 1.84, 2.3, 0.26, 4.5, 0.75, 2.28, 1.8, 0.84, 2.3, 1.6, 3.0, 2.3, 2.17, -0.04, 0.54, 2.4, 4.5, 1.88, 1.47, 0.69, 1.91, 0.61, 1.6, 1.8, 0.73, 0.9, 0.58, 1.6, 1.17, 1.1, 1.8, 0.71, 0.36, 1.9, 0.52, 2.46, 5.0, 1.0, 0.84, 0.58, 4.7, 4.2, 2.26, 1.9, 2.4000001, 1.2, 1.68, 2.02, 0.42, 4.0, 1.21, 2.96, 1.41, 1.85000002, 0.08, 2.1, 4.05, 0.36, 1.5, 2.1, 4.4, 2.0, 2.12, 3.71, 0.59, 1.66, 1.77, 0.39, -0.45, 2.6, 1.06, 1.35, 1.0, 1.98, 1.7, 1.63, 4.3, 1.96, 0.71, 2.6, 0.94, 4.1, 4.7, 4.6, 1.24, 1.79999995, 1.87, 4.4, 1.25, 2.8, 2.04999995, 0.87, 0.74, 2.26, 1.43, 0.75, 1.56, 0.65, -0.32, 1.9, 0.16, 1.54, 1.62, 4.5, 4.1, 6.0, 1.87, 0.8, 2.23000002, 2.4, 1.12, 2.4, 3.3, 0.87, 1.84, 2.01999998, 1.9, 0.51, 1.1, 4.6, 1.59, 0.44, 0.84, 0.81, 4.4, 0.55, 4.6, 1.85, 1.33, 2.0, 0.22, 1.8, 0.56, 0.98, 1.2, 1.6, 2.6, 0.85, 0.87, 2.82, 2.32, 0.79, 0.49, 1.87, 1.65, 2.0, 2.5, 1.22, 1.88, 1.4, 4.6, 4.6, 4.0, 3.0, 2.2, 2.03, 0.4, 1.26, 1.75999999, 1.19, 4.4, 4.5, 2.1, 0.12, -0.08, 2.04999995, 2.35, 2.21, 0.47, 3.3, 1.39, 1.18, 0.47, 0.57, 2.18, 1.1, 0.35, 1.14, -0.08, 1.87, 2.0, 2.24, 1.6, 1.85000002, -0.05, 0.56, 0.8, 0.54, 1.9, 1.73000002, 1.9, 1.82, 1.53, 0.42, 0.1, 1.48, 3.8, 2.00999999, 0.45, 1.74000001, 3.33, 1.53, 0.36, 2.0, 0.36, 2.07, -0.9, 1.49, 2.14, 2.22, 1.5, 1.9, 0.37, 1.54, 0.92, 2.26, 0.83, 0.55, 0.04, 1.61, 1.46, 1.79999995, 1.14, 2.84, 0.72, 0.11, 2.09, 1.01, 2.38, 1.56, 0.8, 1.55, 1.87, 2.1, 2.39, 1.16, 4.4, 0.8, 1.09, 1.68, 0.52, 0.9, 1.03, 0.4, 2.25999999, 2.14, 2.0, 1.64, 3.27, 0.62, 1.69, 1.5, 4.5, 1.41, 1.73, 1.99, 0.85, 0.56, 1.71, -0.55, 1.46, 4.4, 3.8, 0.95, 0.7, 0.95, 1.51, 0.52, 0.72, 0.17, 2.3, 1.98, 2.82, 2.44, 0.81, 1.06, 0.48, 0.41, 0.36, 1.31, 1.44, 0.77, 1.86000001, 1.55, 2.33, 5.0, 1.45, 0.72, 2.1, 0.83, 1.18, 3.09, 1.6, 2.2, 2.03999996, 4.5, 0.49, 1.47, 0.81, 1.73000002, 4.8, 1.6, 0.36, 1.42, 1.42, 4.0, 1.85000002, 5.0, 0.64, 1.8, 0.16, 4.7, 5.0, 1.9, 2.23, 0.8, 1.5, -0.55, 0.5, 2.01999998, 1.24, 1.91, 4.3, 3.2, 0.67, 1.46, 1.82000005, 2.57, 4.0, 1.0, 4.3, 2.94, 1.53, 0.76, 1.52, 1.9, 0.81, 0.85, 0.8, 1.87, 4.3, -0.1, 4.9, 1.58, 2.19000006, 0.8, 1.07, 1.64, 0.6, 6.0, 5.1, 1.14, 4.4, 0.85, 4.4, 1.52, 1.46, 4.2, 1.33, 1.85000002, 1.67, 1.0, 3.06, 2.0, 1.97, 0.49, 2.52, 2.1, 2.01999998, 1.01, 1.2, 0.31, 0.22, 1.1, 0.69, 1.7, 3.1, 0.25, 1.4, 2.9, 1.6, 1.4, 2.3, 0.5, 0.94, 4.6, -0.08, 3.1, 1.87, 1.1, 0.37, 2.5, 1.5, 2.0, 5.1, 1.49, 1.54, 1.4, 0.37, 1.31, 2.20000005, 0.54, 0.7, 4.7, 0.35, 1.8, 1.7, 2.1, 0.86, 0.51, 1.1, 1.85000002, 1.7, 0.48, 2.22, 4.1, 0.94, 4.2, 4.2, 0.47, 3.0, 2.1, 2.3, 2.08, 1.54, 0.5, 1.6, 2.3, 1.79, 2.0, 1.1, 1.72, 4.4, 0.52, 1.6, 1.0, 1.62, 2.6, 2.21000004, 0.92, 1.12, 0.9, 1.1, 1.3, 0.85, 1.36, 4.4, 1.79, 1.22, 1.66, 1.57, 0.37, 1.7, 0.1, 2.2, 5.6, 0.79, 0.45, 0.73, 0.21, 1.3, 1.55, 1.84, 2.16000009, 1.1, 0.9, 1.0, 1.7, 0.2, 1.6, 0.85, 1.6, 1.39, 1.17, 4.2, 2.0, 1.7, 1.7, 4.4, 4.5, 1.9, 2.02999997, 0.31, 0.77, 0.84, 1.53, 1.0, 1.13, 1.5, 2.2, 0.84, 4.3, 3.1, 2.0, 1.9, 2.3, 1.02, 3.35, 0.75, 2.16, 4.0, 1.1, 1.35, 1.1, 0.85, 1.08, 0.62, 4.5, 0.48, 1.8, 1.3, 3.1, 0.86, 1.06, 2.36999989, 4.3, 1.8, 4.1, 0.96, -0.1, 1.13, 1.98000002, 0.63, 2.2, -0.03, 2.13, 4.3, 4.0, 4.2, 2.32, 0.74, 2.8, 3.6, 1.47, 0.34, 0.65, 2.29, 4.9, -0.01]
</pre>
</div>
</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[62]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mag_ranges</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">cut</span><span class="p">(</span><span class="n">Mag</span><span class="p">,</span> <span class="mi">9</span><span class="p">,</span> <span class="n">right</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">labels</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Group A&#39;</span><span class="p">,</span> <span class="s1">&#39;Group B&#39;</span><span class="p">,</span> <span class="s1">&#39;Group C&#39;</span><span class="p">,</span> <span class="s1">&#39;Group D&#39;</span><span class="p">,</span> <span class="s1">&#39;Group E&#39;</span><span class="p">,</span> <span class="s1">&#39;Group F&#39;</span><span class="p">,</span> <span class="s1">&#39;Group G&#39;</span><span class="p">,</span> <span class="s1">&#39;Group H&#39;</span><span class="p">,</span> <span class="s1">&#39;Group I&#39;</span><span class="p">],</span> <span class="n">retbins</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">precision</span><span class="o">=</span><span class="mi">3</span><span class="p">,</span> <span class="n">include_lowest</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">ordered</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">mag_ranges</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[62]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>([&#39;Group C&#39;, &#39;Group B&#39;, &#39;Group D&#39;, &#39;Group E&#39;, &#39;Group C&#39;, ..., &#39;Group B&#39;, &#39;Group B&#39;, &#39;Group D&#39;, &#39;Group G&#39;, &#39;Group B&#39;]
 Length: 9134
 Categories (9, object): [&#39;Group A&#39; &lt; &#39;Group B&#39; &lt; &#39;Group C&#39; &lt; &#39;Group D&#39; ... &#39;Group F&#39; &lt; &#39;Group G&#39; &lt; &#39;Group H&#39; &lt; &#39;Group I&#39;],
 array([-1.21      , -0.24222222,  0.72555556,  1.69333333,  2.66111111,
         3.62888889,  4.59666667,  5.56444444,  6.53222222,  7.50871   ]))</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[63]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#labels = [&#39;Group A&#39;, &#39;Group B&#39;, &#39;Group C&#39;, &#39;Group D&#39;, &#39;Group E&#39;, &#39;Group F&#39;, &#39;Group G&#39;, &#39;Group H&#39;, &#39;Group I&#39;]</span>
<span class="n">ranges</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">1.5</span><span class="p">,</span> <span class="o">-</span><span class="mf">0.5</span><span class="p">,</span>  <span class="mf">0.5</span><span class="p">,</span>  <span class="mf">1.5</span><span class="p">,</span>  <span class="mf">2.5</span><span class="p">,</span>
         <span class="mf">3.5</span><span class="p">,</span>  <span class="mf">4.5</span><span class="p">,</span>  <span class="mf">5.5</span><span class="p">,</span>  <span class="mf">6.5</span><span class="p">,</span>  <span class="mf">8.0</span><span class="p">]</span>
<span class="n">MagRange</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">earthquakes</span><span class="p">[</span><span class="s1">&#39;mag&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="n">pd</span><span class="o">.</span><span class="n">cut</span><span class="p">(</span><span class="n">earthquakes</span><span class="o">.</span><span class="n">mag</span><span class="p">,</span> <span class="n">ranges</span><span class="p">))</span><span class="o">.</span><span class="n">count</span><span class="p">())</span>
<span class="n">MagRange</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[63]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mag</th>
    </tr>
    <tr>
      <th>mag</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>(-1.5, -0.5]</th>
      <td>68</td>
    </tr>
    <tr>
      <th>(-0.5, 0.5]</th>
      <td>1079</td>
    </tr>
    <tr>
      <th>(0.5, 1.5]</th>
      <td>3628</td>
    </tr>
    <tr>
      <th>(1.5, 2.5]</th>
      <td>2895</td>
    </tr>
    <tr>
      <th>(2.5, 3.5]</th>
      <td>506</td>
    </tr>
    <tr>
      <th>(3.5, 4.5]</th>
      <td>573</td>
    </tr>
    <tr>
      <th>(4.5, 5.5]</th>
      <td>354</td>
    </tr>
    <tr>
      <th>(5.5, 6.5]</th>
      <td>28</td>
    </tr>
    <tr>
      <th>(6.5, 8.0]</th>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[74]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig2</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">()</span>

<span class="n">MagPie</span> <span class="o">=</span> <span class="n">MagRange</span><span class="o">.</span><span class="n">plot</span><span class="o">.</span><span class="n">pie</span><span class="p">(</span><span class="n">y</span><span class="o">=</span><span class="s1">&#39;mag&#39;</span><span class="p">,</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax</span><span class="p">,</span> <span class="n">labels</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;A&#39;</span><span class="p">,</span><span class="s1">&#39;B&#39;</span><span class="p">,</span><span class="s1">&#39;C&#39;</span><span class="p">,</span><span class="s1">&#39;D&#39;</span><span class="p">,</span><span class="s1">&#39;E&#39;</span><span class="p">,</span><span class="s1">&#39;F&#39;</span><span class="p">,</span><span class="s1">&#39;G&#39;</span><span class="p">,</span><span class="s1">&#39;H&#39;</span><span class="p">,</span><span class="s1">&#39;I&#39;</span><span class="p">],</span> <span class="n">autopct</span><span class="o">=</span><span class="s1">&#39;</span><span class="si">%1.2f%%</span><span class="s1">&#39;</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span><span class="mi">15</span><span class="p">))</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Magnitude Ranges&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">labels</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Group A: -1.49 to -0.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group B: -0.49 to 0.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group C: 0.51 to 1.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group D: 1.51 to 2.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group E: 2.51 to 3.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group F: 3.51 to 4.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group G: 4.51 to 5.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group H: 5.51 to 6.5&#39;</span><span class="p">,</span> <span class="s1">&#39;Group I: 6.51 to 8.0&#39;</span><span class="p">],</span> <span class="n">loc</span><span class="o">=</span><span class="s1">&#39;upper left&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">yaxis</span><span class="o">.</span><span class="n">label</span><span class="o">.</span><span class="n">set_color</span><span class="p">(</span><span class="s1">&#39;white&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">tight_layout</span><span class="p">()</span>


<span class="c1">#&#39;Group A: -1.49 to -0.5&#39;, &#39;Group B: -0.49 to 0.5&#39;, &#39;Group C: 0.51 to 1.5&#39;, &#39;Group D: 1.51 to 2.5&#39;, &#39;Group E: 2.51 to 3.5&#39;, &#39;Group F: 3.51 to 4.5&#39;, &#39;Group G: 4.51 to 5.5&#39;, &#39;Group H: 5.51 to 6.5&#39;, &#39;Group I: 6.51 to 8.0&#39;</span>
<span class="c1">#magnitudes = pd.DataFrame({&#39;ranges&#39;: [-1.21, -0.24222222, 0.72555556, 1.69333333, 2.66111111, 3.62888889, 4.59666667, 5.56444444, 6.53222222, 7.50871]},</span>
                  <span class="c1">#index=[, &#39;Group J&#39;])</span>
<span class="c1">#plot = magnitudes.plot.pie(subplots=True, figsize=(5, 5))</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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Hh5+YuHLfv36HV+4cGHnGTNmhEdGRpY+8MADJxUCr732WqdRo0YVBgQEnBjOcf311x9NSkrqXVJSsv/Xv/5135kzZ+acabrI9OnTe//rX/8KPX78uFf37t2H3HjjjYefeeaZrKVLl4Z888037c9UcEyfPr1PcnJyoCT99re/zRoyZMgpoxsmT5589Jprrun/wQcfdHz22Wf3//3vf9+fmJgY8dxzz4V17ty5YvHixXsbOockPf300xlTpkzpP3fu3F6DBg0qvueeew5L0hdffBH4/PPPd12xYsW+rVu3+s+cOTPcMAxZlqV77733wLBhw46f6dgAAAAAAM9g1Dclojls27Ztb3x8/OEWOZkNUlNT/caPHx+1c+fO7XZnaYu2bdvWJT4+PsLuHAAAAACAluUxU0UAAAAAAEDrQ3HRRGJiYsoYbQEAAAAAQNOiuAAAAAAAAG6L4gIAAAAAALgtigsAAAAAAOC2KC4AAAAAAIDb8rHtzEkhw5r2ePmbz7RJenq6z4wZM/ps2bIlKCQkpMLX19eaNWvWgWnTph1t0iwNmDx5csT69euDg4ODK0tLS41JkyYdefrpp7PP5hgpKSl+1113Xb/8/HyfwYMHF7/99tt7/P39672v7ZEjR7xiY2MHjxs37ujixYv3S9J7770X/NBDD/UuLy/3Mk3z2IoVK/b6+vqetN+6desC0tPT/aZMmZJ/Ntl+97vfhS1durSLl5eXnn766f2TJ08uqLvNrFmzer722mtdQkNDKyRpzpw5mWd7HgAAAACAZ/CYERcul0sTJkwYkJCQUJSRkeHcvn37jjfeeGN3enq6X91ty8vLmzXL3LlzM1JSUpK3b9+evGLFii4pKSmnZGjIrFmzet91110H9+3b931ISEjFc8891+V0295///29RowYUVjzdWVlpX7zm99Evv7667t37ty5vW/fvmV/+9vfTtl/06ZNgf/5z39CzibX5s2b/d95553Q1NTU7R9++GHavffe27eioqLebadPn34wJSUlOSUlJZnSAgAAAABwOh5TXKxcuTLY19fXmj17dk7NY9HR0WUPP/zwIUlasGBB5yuvvLLfmDFjBiQkJEQfPHjQe+zYsf2jo6Pj4uPjYzds2BAgVY0WePTRR7vXHCMqKmpQamqqX2pqql9kZOSgSZMmRURHR8eNGzeuX2FhYYOvb3FxsZck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O+64o97CosaCBQt6nO31XH311Uc3bNiw40zb9enTp7QmF6UFAAAAAKCxPKa4WLlyZbCvr681e/bsnJrHoqOjyx5++OFDkrRgwYLOV155Zb8xY8YMSEhIiD548KD32LFj+0dHR8fFx8fHbtiwIUCSZs2a1fPRRx/tXnOMqKioQampqX6pqal+kZGRgyZNmhQRHR0dN27cuH6FhYWnvL5//etfw1588cX9oaGhLknq3Llz5d13333a0RaS9O6773a88cYbc728vHTZZZcdKygo8Nm3b59vY6+9V69eFZdcckmxr6/vaRuSGTNm9CotLfWKjY2NmzhxYqQkJSUldY+KihoUFRU16LHHHutW336XXXbZsfDw8OZregAAAAAAHs1jigun0xkwZMiQU6ZX1Pbtt98GLV++fM/69evTZs+e3TM+Pr44LS0t+fHHH89MTEyMPNM59u7d6z99+vSctLS05ODgYNf8+fO71n4+Ly/P69ixY96DBg0qrW//e++9t+fSpUtD6j6enZ3tGxERUVbzdY8ePcpOV1zMmTOnV3R0dNytt97ap6SkxDhT5hovvPBCZrt27VwpKSnJ77333p4vv/wycNmyZZ03b968Y9OmTTsWL17c9auvvgpo7PHqysjI8Bs4cGDcBRdcEPPhhx8GnetxAAAAAACexWOKi7puuummvjExMXGDBw8eWPNYQkJCQffu3SslaePGjcG33nprriRNnDix8OjRoz65ubneDR0zLCys7IorrjhWffzcdevWnfQG3bIsGcbpu4Rnn30268Ybb8yv+3h9U0nqO84zzzyTuXv37u+3bdu2Iy8vz/sPf/hDWEN5G7J69eqgn//850c7dOjgCgkJcV111VV5n3/+efC5HKtv377le/bs+W7Hjh3JzzzzTPqvf/3rfkeOHPHY7z0AAAAAQON5zJtH0zRLvvvuu8Car5csWbJ/9erVaXl5eScWKA0MDHTVfH6assDy8fGxXK4Tm6m0tNSo9Xzd7U/6OjQ01BUQEOBKTk4+ZV2NhvTs2bN87969J/bJzs7269u37ynTM8LDw8u9vLwUEBBg3XLLLbmbN29ufzbnqe1M626cjYCAACssLKxSkhISEor79u1b+v333/s32QkAAAAAAG2WxxQXEyZMKCwtLTXmzZt3YvpGUVHRaa9/5MiRhYsWLeosSatWrQru1KlTRWhoqCsiIqJ069at7SVp7dq1gZmZme1q9snOzvb75JNP2kvSsmXLQkeNGlVU97j33ntv9vTp08NrRhwcOXLE66mnnurSUPaJEyceXbp0aWeXy6VPP/20fXBwcGV960rUTB9xuVx65513Og4cOLDkTK9LbT4+PlZNETNmzJii999/v2NhYaFXQUGB1/vvv9/ppz/9aeHZHK9GVlaWT0VFhSQpOTnZb+/eve1iYmLqnS4DAAAAAEBttt0OtTG3L21KXl5eWrly5Q8zZ87ss2DBgrDQ0NCKwMDAyqSkpIz6tp83b17W1KlTI6Kjo+MCAgJcr7766h5JmjZtWt7SpUs7x8bGxg0dOvRYeHj48Zp9+vXrd3zhwoWdZ8yYER4ZGVn6wAMP5NQ97uzZs3OKioq8zj///DhfX1/Lx8fHuvvuuw9IVWtcXHDBBcfqThe57rrr8v/zn/+EhIeHDw4ICHC9/PLLe2ueu+SSSwY4HI59ERER5VOmTIk8cuSIj2VZRlxcXPHixYv3SdL+/ft9Lrjggrhjx455G4Zhvfjii9137Njxfc0CoTVuvPHGnIEDB8YNHjy4+L333tszderU3PPPP3+gJN100005P/nJT04pQqZPn977X//6V+jx48e9unfvPuTGG288/Mwzz2QtXbo05Jtvvmn/7LPPZn300UdBc+fO7eXt7W15e3tbzz777L6aKTkAAAAAADTEaMopAQ3Ztm3b3vj4+MMtcjIbpKam+o0fPz5q586d2+3O0hZt27atS3x8fITdOQAAAAAALctjpooAAAAAAIDWh+KiicTExJQx2gIAAAAAgKZFcQEAAAAAANwWxQUAAAAAAHBbFBcAAAAAAMBtUVwAAAAAAAC35WPXiXfEDhzWlMcbmLJj85m2SU9P95kxY0afLVu2BIWEhFT4+vpas2bNOjBt2rSjTZmlIZMnT45Yv359cFBQUGVpaanXeeedV/TMM89kRkZGlje03wcffBB0//3390lLSwt86aWXdt9888159W134YUXxhw6dMjX39/fJUmffvppWq9evSoas//hw4e9X3755dCHHnoop7HXs2vXLt8bb7wxMicnx9fLy0uJiYk5f/jDHw7V3W7VqlXBN9xwQ/9evXqVSdL48ePznnrqqezGngcAAAAA4Jk8ZsSFy+XShAkTBiQkJBRlZGQ4t2/fvuONN97YnZ6e7ld32/LyBjuEH23u3LkZqampybt37/5+6NChxT/96U9jjh8/bjS0T79+/coWLVq0d8KECblnOv7ixYt3p6SkJKekpCT36tWrorH75+bmer/yyivdzuZafH199fTTT2fs3r17+zfffLPjlVde6bZ582b/+rYdPnx4UU0uSgsAAAAAQGN4THGxcuXKYF9fX2v27NknRhNER0eXPfzww4ckacGCBZ2vvPLKfmPGjBmQkJAQffDgQe+xY8f2j46OjouPj4/dsGFDgCTNmjWr56OPPtq95hhRUVGDUlNT/VJTU/0iIyMHTZo0KSI6Ojpu3Lhx/QoLCxt8fb28vPTHP/7xUJcuXcrfeuutkIa2jYmJKRsxYkSJl9e5/StrzP73339/7/T09HaxsbFxd9xxR2+Xy6U77rijd1RU1KDo6Oi4l156qVPdfcLDw8svvvjiYknq1KmTq3///iX79+8/pQwCAAAAAOBceExx4XQ6A4YMGVLc0Dbffvtt0PLly/esX78+bfbs2T3j4+OL09LSkh9//PHMxMTEyDOdY+/evf7Tp0/PSUtLSw4ODnbNnz+/a2OyDRkypHjHjh3+kjRlypTwL774IrBxV1W/2267LSI2NjbuwQcf7OFyuRq939NPP53Rp0+f0pSUlOQXX3wxY/HixR2dTmfAjh07tn/66adpjz76aO99+/b5nm7/1NRUv+Tk5MBLLrmkqL7nt2zZEhQTExM3evToqE2bNtU7KgMAAAAAgNo8prio66abbuobExMTN3jw4IE1jyUkJBR07969UpI2btwYfOutt+ZK0sSJEwuPHj3qk5ub693QMcPCwsquuOKKY9XHz123bl1QY7JYlnXi8xUrVuwbPXp0gwVLQ1asWLE7LS0t+euvv05Zt25d0AsvvND5XI/15ZdfBl933XVHfHx81KdPn4oRI0YUrV27tt5SJT8/32vSpEn9n3jiifTQ0NBT2pJRo0Yd27dv33epqanJM2fOPDR58uQB55oLAAAAAOA5PKa4ME2z5LvvvjvxpnvJkiX7V69enZaXl3digdLAwMATb7hrlwk1DMOwfHx8rNqjGEpLS41az9fdvlHZnE5nYFxcXEnjrqRhNYt8durUyTVlypQjGzdubH+ux6rvNahPaWmpcdVVV/W/9tprjyQmJh6tb5vQ0FBXSEiIS5KmTJmSX1FRYWRnZ9u2OCwAAAAAoHXwmOJiwoQJhaWlpca8efNOTN8oKio67fWPHDmycNGiRZ2lqjtidOrUqSI0NNQVERFRunXr1vaStHbt2sDMzMx2NftkZ2f7ffLJJ+0ladmyZaGjRo2qd8pEDZfLpblz53bLycnxnTx5csGPvcby8nLVlAGlpaXG+++/HzJ48OBGFyIhISGVx44dO/GaXHLJJYVvvfVWaEVFhbKysnw2btwYlJCQcKzuNVx//fXh0dHRx5OSkg6e7tj79+/3qSl8Pv/880CXy6Xu3btXnPVFAgAAAAA8im1/8W7M7UubkpeXl1auXPnDzJkz+yxYsCAsNDS0IjAwsDIpKSmjvu3nzZuXNXXq1Ijo6Oi4gIAA16uvvrpHkqZNm5a3dOnSzrGxsXFDhw49Fh4efrxmn379+h1fuHBh5xkzZoRHRkaWPvDAA/XeVvSRRx7p/cQTT/Q4fvy413nnnXfss88+S/X397ekqjUuZs6cmVN3usiaNWsCr7vuugEFBQXen376acc//elPPXft2rVdkmJjY+NSUlKSS0pKvMaOHRtVXl5uuFwuIyEhoWDWrFk5Z9q/RlhYWOWwYcOKoqKiBo0ZMyb/73//e8a6deuCBg4cOMgwDGvOnDkZffv2Pals+Pjjj4P+/e9/d46KiiqJjY2Nk6Q5c+ZkTpkyJf/JJ5/sKkmzZ8/Oee211zotXLiwm7e3t+Xv7+9avHjx7nNdaBQAAAAA4DmMxk4H+LG2bdu2Nz4+/nCLnMwGqampfuPHj4/auXPn9jNvjbO1bdu2LvHx8RF25wAAAAAAtCz+5A0AAAAAANwWxUUTiYmJKWO0BQAAAAAATYviAgAAAAAAuC2KCwAAAAAA4LYoLgAAAAAAgNuiuAAAAAAAAG7Lx64TPz/9s2FNebyZ/xiz+UzbpKen+8yYMaPPli1bgkJCQip8fX2tWbNmHZg2bdrRpszSkMmTJ0esX78+ODg4uFKSAgICXFu2bEk53fa7du3yvfHGGyNzcnJ8vby8lJiYmPOHP/zhUN3tVq1aFXzDDTf079WrV5kkjR8/Pu+pp57KlqRrr7024tNPPw3p3LlzxekWEF2yZEnHuLi448OGDTve2Gt58sknu7788stdvby81L59+8p//vOf++rb/8ILL4w5dOiQr7+/v0uSPv3007RevXpVNPY8AAAAAADPZVtx0dJcLpcmTJgwYOrUqbkrV67cI0lpaWl+b775Zse625aXl8vX17fZssydOzfj5ptvzmvMtr6+vnr66aczLr744uK8vDyv8847L+7nP/95QX0FwfDhw4s+//zzXXUfv+WWWw7fc889h26++ebI053n3//+d8eKior8sykubrvtttzZs2fnSNLSpUtD7r333j5ffvnlzvq2Xbx48e7Ro0cXN/bYAAAAAABIHjRVZOXKlcG+vr5WzRttSYqOji57+OGHD0nSggULOl955ZX9xowZMyAhISH64MGD3mPHju0fHR0dFx8fH7thw4YASZo1a1bPRx99tHvNMaKiogalpqb6paam+kVGRg6aNGlSRHR0dNy4ceP6FRYW/ujXNzw8vPziiy8ulqROnTq5+vfvX7J//36/sznGlVdeWdS1a9fTjnD4+OOP23/yyScdH3nkkd6xsbFx27dvb7du3bqA+Pj42Ojo6LjLL7+8f05Ojnfd/UJDQ101nxcVFXkbhnE2sQAAAAAAOCOPKS6cTmfAkCFDGvyL/7fffhu0fPnyPevXr0+bPXt2z/j4+OK0tLTkxx9/PDMxMfG0oxVq7N2713/69Ok5aWlpycHBwa758+d3rW+7moIgNjY2buLEiZGS9MUXXwROmTIlvKHjp6am+iUnJwdecsklRfU9v2XLlqCYmJi40aNHR23atMn/THlrXH755cfGjh17dO7cuRkpKSnJgwYNKv31r38d+ec//zkjLS0tedCgQSW//e1ve9a371/+8peuffr0GfzHP/6x9/PPP7//dOe47bbbImJjY+MefPDBHi6X63SbAQAAAABwEo8pLuq66aab+sbExMQNHjx4YM1jCQkJBd27d6+UpI0bNwbfeuutuZI0ceLEwqNHj/rk5uaeMuqgtrCwsLIrrrjiWPXxc9etWxdU33Y1BUFKSkrye++9t0eSRo8eXbxixYp9pzt2fn6+16RJk/o/8cQT6bVHOtQYNWrUsX379n2XmpqaPHPmzEOTJ08e0JjXoT65ubnehYWF3ldddVWRJN1+++2569evr/dafve73+Wkp6d/n5SUlPHHP/6xR33brFixYndaWlry119/nbJu3bqgF154ofO5ZgMAAAAAeBaPKS5M0yz57rvvAmu+XrJkyf7Vq1en5eXlnVjnIzAw8EQhYFnWKccwDMPy8fGxao8YKC0tNWo9X3f7JsleWlpqXHXVVf2vvfbaI4mJiUfr2yY0NNQVEhLikqQpU6bkV1RUGNnZ2S22hsntt99+5OOPP+5Y33ORkZHlUtVUlylTphzZuHFj+5bKBQAAAABo3TymuJgwYUJhaWmpMW/evBPTN4qKik57/SNHjixctGhRZ6nqjh2dOnWqCA0NdUVERJRu3bq1vSStXbs2MDMzs13NPtnZ2X6ffPJJe0latmxZ6KhRo+qd0nE2XC6Xrr/++vDo6OjjSUlJB0+33f79+31qCpXPP/880OVyqXv37o2+c0dQUFBlQUGBlyR17ty5skOHDpUffvhhkCS98sornS+66KJTrsXpdJ649hUrVoSEh4eX1t2mvLxcNQVKaWmp8f7774cMHjy4pLG5AAAAAACezahvZEFz2LZt2974+PjDLXKy09i3b5/vzJkz+2zZsqV9aGhoRWBgYOVtt92Wc/vtt+ctWLCg86ZNm9ovXrx4vyQdPHjQe+rUqRHp6entAgICXP/85z/3jRgxoqSoqMj42c9+NiA3N9d36NChxzZu3Bj0wQcf7JSkn//851EjRowo3LRpU1BkZGTpW2+9tSc4OPikaR11b4cqSVu3bt2xcePGgOeff75r3eki//3vf4PGjRsXExUVVeLlVdWzzJkzJ3PKlCn5Tz75ZFdJmj17ds6f//znrgsXLuzm7e1t+fv7u5566qn0yy+//JgkTZgwIXL9+vXBeXl5Pp07d6546KGHsu67776T/l189NFH7e+8884IPz8/66233vohPz/f68477wwvKSnx6tu3b+ny5cv3du3atbL2PjfffHOfL7/8soOPj48VEhJS8fzzz+8fPnz4cUmKjY2NS0lJSS4oKPC66KKLYsrLyw2Xy2UkJCQUvPTSS+k+Pmc3GGTbtm1d4uPjI85qJwAAAABAq+dRxUVzSk1N9Rs/fnzUzp07t9udpS2iuAAAAAAAz+QxU0UAAAAAAEDrQ3HRRGJiYsoYbQEAAAAAQNOiuAAAAAAAAG6L4gIAAAAAALgtigsAAAAAAOC2KC4AAAAAAIDb8rHrxE9PGT+sKY93/4pVm8+0TXp6us+MGTP6bNmyJSgkJKTC19fXmjVr1oFp06YdbcosDZk8eXLE+vXrg4ODgysl6Ve/+tXhRx555FB9237++eeBd955Z4QkWZalhx9+OKu+rLNmzer52muvdQkNDa2QpDlz5mROmTIl/8CBA96/+MUv+judzvbXXHNN7uLFi/fXd57HHnus23333Xc4ODjYdbbXk5iY2OfNN9/sUlxcvKW+5729vYdFRUWVSFLPnj3LPvvss11new4AAAAAgOeyrbhoaS6XSxMmTBgwderU3JUrV+6RpLS0NL8333yzY91ty8vL5evr22xZ5s6dm3HzzTfnnWm74cOHH3c6ncm+vr7at2+f73nnnRd3ww03HK0v2/Tp0w8+9thjB2s/FhgYaD322GNZ27ZtC/j+++8DTneeF198sfvtt99+5GyLiy+++CIwPz+/we+hdu3auVJSUpLP5rgAAAAAANTwmKkiK1euDPb19bVmz56dU/NYdHR02cMPP3xIkhYsWND5yiuv7DdmzJgBCQkJ0QcPHvQeO3Zs/+jo6Lj4+PjYDRs2BEhVoxseffTR7jXHiIqKGpSamuqXmprqFxkZOWjSpEkR0dHRcePGjetXWFj4o17f4OBgV01JUVJSYhiGcVb7d+jQwfWzn/2syN/f/7SFxNy5c7sdOnTI95JLLokeMWJEtCS9+OKLodHR0XFRUVGD7rzzzl717VdRUaEHH3yw93PPPZdxVqEAAAAAADgLHlNcOJ3OgCFDhhQ3tM23334btHz58j3r169Pmz17ds/4+PjitLS05McffzwzMTEx8kzn2Lt3r//06dNz0tLSkoODg13z58/vWt92jzzySO/Y2Ni42NjYuI0bNwY8+eSTXZ988sl6t/3ss8/aDxgwYND5558/6K9//eu+040EeeWVV7pFR0fHXXvttRE5OTneZ8paK8uhbt26la9ZsyZtw4YNaXv37vVNSkrqtXr16rTk5OTtW7Zsab9kyZKOdff7y1/+0u3nP//50fDw8PKGjl9WVuY1ePDggfHx8bH1HQcAAAAAgIZ4THFR10033dQ3JiYmbvDgwQNrHktISCjo3r17pSRt3Lgx+NZbb82VpIkTJxYePXrUJzc3t8FCICwsrOyKK644Vn383HXr1gXVt93cuXMzUlJSklNSUpIvvPDCktmzZ+fUHglS25gxY47t2rVr+9q1a3fMnz+/R3Fx8SnDLu67775D+/btc+7YsSM5LCysfMaMGX0a/0qcbO3ate1HjhxZ2LNnzwpfX19NmTLlyJo1a066jr179/r++9//7vT73/++3rU5atu1a9d333///Y7ly5fvfuihh/ps37693blmAwAAAAB4Ho8pLkzTLPnuu+8Ca75esmTJ/tWrV6fl5eWdWKMhMDDwxJQKy7JOOYZhGJaPj4/lcv1v5kVpaalR6/m62zdZ/vPPP/94YGBg5aZNm05Zq6JPnz4VPj4+8vb21l133ZWzdevW9ud6nvquu67169cH7tu3zz8iIsLs1auXefz4ca++ffsOrm/biIiIckmKi4srGzlyZOHGjRsD69sOAAAAAID6eExxMWHChMLS0lJj3rx5J6ZkFBUVnfb6R44cWbho0aLOkrRq1argTp06VYSGhroiIiJKa4qBtWvXBmZmZp4YQZCdne33ySeftJekZcuWhY4aNarox2ROSUnxKy+vmomRlpbmt2fPHv+oqKiyutvt27fvxPyR119/vWNMTEzJ2Zynffv2lfn5+V6SNHr06GMbNmwIzs7O9qmoqNCbb74Zeumll550Hddff33+4cOHt2VmZjozMzOd/v7+rv37939f97g5OTneJSUlhiRlZ2f7bNq0KWjIkCFnlQ0AAAAA4Nlsu6tIY25f2pS8vLy0cuXKH2bOnNlnwYIFYaGhoRWBgYGVSUlJ9S4uOW/evKypU6dGREdHxwUEBLheffXVPZI0bdq0vKVLl3aOjY2NGzp06LHw8PDjNfv069fv+MKFCzvPmDEjPDIysvSBBx6od/pHXTXrW9SdLvLpp58GjR8/voePj4/l5eVlPf300/t79OhRIUlTpkwJnzlzZs7o0aOL77nnnt7JyckBktS7d++yRYsW7as5Rq9evcyioiLv8vJy47///W/H999/P23YsGHHa58nMTHx8JVXXhnVrVu38g0bNqQ9+uijmZdcckm0ZVnGZZddlv+rX/3qaKNeZFXdaeT555/vumLFin1bt271nzlzZrhhGLIsS/fee++BuucGAAAAAKAhRmOmBjSFbdu27Y2Pjz/cIiezQWpqqt/48eOjdu7cud3uLG3Rtm3busTHx0fYnQMAAAAA0LI8ZqoIAAAAAABofSgumkhMTEwZoy0AAAAAAGhaFBcAAAAAAMBtUVwAAAAAAAC3RXEBAAAAAADcFsUFAAAAAABwWz52nTjjoS+HNeXxej+RsPlM26Snp/vMmDGjz5YtW4JCQkIqfH19rVmzZh2YNm3a0abMciZJSUndHQ5HF19fX8swDCUkJBQ8//zzme3atTvjvWkXLVrU6ZZbbum3Zs2aHaNHjy6u+/yFF14Yc+jQIV9/f3+XJH366adpvXr1qvjggw+C7r///j5paWmBL7300u6bb745r+6+hw8f9n755ZdDH3rooZyzuZ5evXqZ7du3r/Ty8pKPj4/1/fff76i7zapVq4JvuOGG/r169SqTpPHjx+c99dRT2WdzHgAAAACA57GtuGhpLpdLEyZMGDB16tTclStX7pGktLQ0vzfffLNj3W3Ly8vl6+vbLDmefPLJrp9++mmHb775JqVLly6Vx48fNx577LHux44dM85UXOTl5Xk9//zz3YYMGXKsoe0WL168u26p0a9fv7JFixbtfeKJJ7qfbr/c3FzvV155pdvZFheStGbNmrQePXpUNLTN8OHDiz7//PNdZ3tsAAAAAIDn8pipIitXrgz29fW1Zs+efeJNeXR0dNnDDz98SJIWLFjQ+corr+w3ZsyYAQkJCdEHDx70Hjt2bP/o6Oi4+Pj42A0bNgRI0qxZs3o++uijJ978R0VFDUpNTfVLTU31i4yMHDRp0qSI6OjouHHjxvUrLCw85fV95plnerz00kv7unTpUilJ/v7+1p///OcDoaGhrjNdw/3339/r/vvvP9CYkRl1xcTElI0YMaLEy+v0/8rvv//+3unp6e1iY2Pj7rjjjt4ul0t33HFH76ioqEHR0dFxL730UqezPS8AAAAAAD+GxxQXTqczYMiQIadMrajt22+/DVq+fPme9evXp82ePbtnfHx8cVpaWvLjjz+emZiYGHmmc+zdu9d/+vTpOWlpacnBwcGu+fPnd639fF5enldxcbFXbGxs2emOMWXKlPAvvvgisO7jX331VUBmZqbfDTfckH+mHLfddltEbGxs3IMPPtjD5TpjH3LC008/ndGnT5/SlJSU5BdffDFj8eLFHZ1OZ8COHTu2f/rpp2mPPvpo73379tU7FOWyyy6LGjRo0MCnnnqqy+mOv2XLlqCYmJi40aNHR23atMm/0cEAAAAAAB7LY6aK1HXTTTf13bhxY5Cvr++JNRkSEhIKunfvXilJGzduDH777bd3SdLEiRMLf/Ob3/jk5uZ6N3TMsLCwsiuuuOJY9fFzFyxY0E3SwZrnLcuSYRgntn/77bc7PPzww70LCwu9X3311d2XX375sRUrVuyre9zKykrdd999fZcsWbLnTNe1YsWK3ZGRkeV5eXle48eP7//CCy90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"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[76]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig2</span><span class="o">.</span><span class="n">savefig</span><span class="p">(</span><span class="s1">&#39;Figure2_MagRange.jpg&#39;</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[99]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">dfDepth</span> <span class="o">=</span> <span class="n">earthquakes</span><span class="p">[[</span><span class="s1">&#39;depth&#39;</span><span class="p">]]</span>
<span class="n">dfDepth</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[99]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>depth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.97</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.98</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.63</td>
    </tr>
    <tr>
      <th>3</th>
      <td>10.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.78</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>9129</th>
      <td>4.44</td>
    </tr>
    <tr>
      <th>9130</th>
      <td>3.47</td>
    </tr>
    <tr>
      <th>9131</th>
      <td>8.37</td>
    </tr>
    <tr>
      <th>9132</th>
      <td>121.09</td>
    </tr>
    <tr>
      <th>9133</th>
      <td>4.29</td>
    </tr>
  </tbody>
</table>
<p>9134 rows × 1 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[106]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">dfDepth2</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">dfDepth</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;earthquake&#39;</span><span class="p">,</span> <span class="s1">&#39;chemical explosion&#39;</span><span class="p">,</span> <span class="s1">&#39;explosion&#39;</span><span class="p">,</span> <span class="s1">&#39;ice quake&#39;</span><span class="p">,</span> <span class="s1">&#39;other event&#39;</span><span class="p">,</span> <span class="s1">&#39;quarry blast&#39;</span><span class="p">,</span> <span class="s1">&#39;sonic boom&#39;</span><span class="p">])</span>
<span class="n">dfDepth2</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[106]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>earthquake</th>
      <th>chemical explosion</th>
      <th>explosion</th>
      <th>ice quake</th>
      <th>other event</th>
      <th>quarry blast</th>
      <th>sonic boom</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9129</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9130</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9131</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9132</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9133</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>9134 rows × 7 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[107]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fig3</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">()</span>
<span class="n">dfDepth2</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span><span class="n">column</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;earthquake&#39;</span><span class="p">,</span> <span class="s1">&#39;chemical explosion&#39;</span><span class="p">,</span> <span class="s1">&#39;explosion&#39;</span><span class="p">,</span> <span class="s1">&#39;ice quake&#39;</span><span class="p">,</span> <span class="s1">&#39;other event&#39;</span><span class="p">,</span> <span class="s1">&#39;quarry blast&#39;</span><span class="p">,</span> <span class="s1">&#39;sonic boom&#39;</span><span class="p">],</span> <span class="n">ax</span><span class="o">=</span><span class="n">ax</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[107]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:&gt;</pre>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span> 
</pre></div>

     </div>
</div>
</div>
</div>

</div>
</body>







</html>


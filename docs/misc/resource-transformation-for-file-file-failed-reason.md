---
title: "Resource transformation for file &#39;file&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_failed"
ms.assetid: 6b537d38-1da9-4f5f-9ae9-1f26e260c2ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resource transformation for file &#39;file&#39; failed. &lt;reason&gt;
.resx ファイルをバイナリの .resources ファイルに変換するために使用されるリソース プロセッサが失敗しました。  特定の原因がある場合は、メッセージの最後に追加されます。  このエラーが発生した場合、ビルド プロセスは失敗します。  
  
 一般に、このエラーは、無効な .resx ファイルが原因で発生します。  たとえば、このファイルがテキスト エディターで開かれ、変更を加えられている可能性があります。  
  
 "項目は既に追加されています。  辞書のキー: 'NewControlName.\<プロパティ名\>' 追加されるキー: 'ControlName.\<プロパティ名\>' "の \<理由\> を受け取った場合は、次の手順を参照してエラーを再現し、修正してください。  
  
### このエラーを再現するには  
  
1.  新しい Windows アプリケーションを作成します。  既定では、Form1 が作成されます。  
  
2.  **\[表示\]** メニューの **\[プロパティ\]** をクリックします。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[Localizable\]** プロパティを `True` に設定します。  
  
4.  **\[プロパティ\]** ウィンドウの **\[Language\]** をクリックし、値を "日本語" に設定します。  
  
5.  ツールボックスから、フォームにボタンをドラッグします。  
  
6.  ボタンの名前を "Button1" から "BUTTON1" に変更します。  
  
7.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
### このエラーを解決するには  
  
1.  **\[ファイル\]** メニューの **\[開く\]** をポイントし、**\[ファイル\]** をクリックします。  
  
2.  Form1.resx ファイルを検索し、**\[OK\]** をクリックします。  Form1.resx が表示されます。  
  
3.  元のキー値を検索して、データ リストから手動で削除します。  たとえば、"Button1" という名前のボタンがあるとします。  このボタンの名前を "BUTTON1" に変更します。  "Button1" および "BUTTON1" のどちらのキー値も Form1.resx に含まれます。  "Button1" のすべてのエントリを削除してから、プロジェクトを再ビルドします。  
  
## 参照  
 [Resources in .Resx File Format](http://msdn.microsoft.com/ja-jp/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)   
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/ja-jp/f793852c-da06-4d52-a826-65f635844772)
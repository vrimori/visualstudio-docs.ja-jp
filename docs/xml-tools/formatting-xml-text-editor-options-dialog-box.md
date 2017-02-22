---
title: "[書式設定] ([オプション] ダイアログ ボックス - [テキスト エディター] - [XML]) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# [書式設定] ([オプション] ダイアログ ボックス - [テキスト エディター] - [XML])
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このダイアログ ボックスでは、XML エディターの書式設定を指定することができます。\[オプション\] ダイアログ ボックスには、\[ツール\] メニューからアクセスできます。  
  
> [!NOTE]
>  これらの設定を使用するには、\[テキスト エディター\] フォルダーを選択し、\[XML\] フォルダーを選択します。次に、\[オプション\] ダイアログ ボックスから \[書式設定\] オプションをクリックします。  
  
## 属性  
 **Preserve manual attribute formatting \(手動による属性の書式設定を保持する\)**  
 属性の書式は再設定されません。これは、既定の設定です。  
  
> [!NOTE]
>  属性が複数行にわたっている場合、エディターは親要素のインデントに対応するように属性の各行にインデントを設定します。  
  
 **Align attributes each on their own line \(行ごとに各属性を配置する\)**  
 最初の属性のインデントに対応するように、2 番目およびそれ以降の行頭を揃えて配置します。XML テキストで属性がどのように並べられるかについて例を次に示します。  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## 自動による書式の再設定  
 **On paste from the Clipboard \(クリップボードから貼り付ける\)**  
 クリップボードから貼り付ける XML テキストの書式を再設定します。  
  
 **On completion of end tag \(終了タグ終了時に書式を再設定\)**  
 終了タグが完了したときに要素の書式を再設定します。  
  
## 混合コンテンツ  
 **既定では、混合コンテンツは保持されます。**  
 エディターで混合コンテンツの書式を再設定するかどうかを指定します。既定では、コンテンツが `xml:space="preserve"` スコープで見つかった場合を除き、エディターは混合コンテンツの書式を再設定しようとします。  
  
 要素にテキストとマークアップが混在して含まれている場合、そのコンテンツは混合コンテンツと見なされます。混合コンテンツを持つ要素の例を次に示します。  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## 参照  
 [XML ドキュメント プロパティと \[プロパティ\] ウィンドウ](../Topic/XML%20Document%20Properties,%20Properties%20Window.md)   
 [XML エディターのコンポーネント](../xml-tools/xml-editor-components.md)
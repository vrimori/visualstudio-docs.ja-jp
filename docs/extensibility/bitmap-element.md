---
title: "ビットマップ要素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ビットマップ、VSCT XML スキーマ要素"
  - "ビットマップ要素 (VSCT XML スキーマ)"
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ビットマップ要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ビットマップを定義します。 ビットマップには、リソースまたはファイルが読み込まれます。  
  
## 構文  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。 GUID と ID コマンドの識別子の GUID です。<br /><br /> ビットマップの guid 属性がすべての VSPackage またはその他のコマンドのグループに関連付けではありません。  ビットマップの定義に対して一意である必要があり、その他の目的は使用しないでします。|  
|resID|GUID と ID コマンドの識別子の ID です。 ResID または href 属性のいずれかが必要です。<br /><br /> ResID 属性は、コマンド テーブルのマージ中にロードするビットマップ ストリップを決定する整数リソース ID です。  コマンド テーブルの読み込む際に、リソース ID で指定したビットマップは、同じモジュールのリソースから読み込まれます。|  
|usedList|ResID 属性があるかどうかに必要です。 ビットマップ ストリップの利用可能なイメージを選択します。|  
|href|ビットマップへのパス。 ResID または href 属性のいずれかが必要です。<br /><br /> インクルード パスでは、結果のバイナリに埋め込むことが示されたイメージ ファイルが検索されます。  コマンド テーブルのマージ中に、イメージがコピーされ、その他のリソースの検索や負荷は必要ありません。  UsedList 属性が存在しない場合は、ストリップ内のすべてのイメージを使用です。 **Note:**  イメージは、.bmp、.gif、.png を含むいくつかの形式のいずれかで指定することがあります。  以前のバージョンのコンパイラでは、部分的に透明のアルファ情報が含まれている 32 ビットのビットマップ イメージはサポートしませんでした。 これらのバージョンの回避策では、.png 形式を使用します。|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[ビットマップ要素](../extensibility/bitmaps-element.md)|ビットマップの要素をグループ化します。|  
  
## 使用例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
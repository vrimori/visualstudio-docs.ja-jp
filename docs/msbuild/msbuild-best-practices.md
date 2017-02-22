---
title: "MSBuild のベスト プラクティス | Microsoft Docs"
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
  - "推奨される手順, MSBuild"
  - "MSBuild, 推奨される手順"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild のベスト プラクティス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild スクリプトを記述するための次のベスト プラクティスを推奨します。  
  
-   既定のプロパティ値は、コマンド ラインで既定値をオーバーライドできるプロパティを宣言するのではなく、`Condition` 属性を使用して処理することをお勧めします。  たとえば、次を使用します。  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   項目を選択するときに、ワイルドカードを避けます。  代わりに、ファイルを明示的に指定します。  ファイルを追加または削除する場合に発生する可能性のあるエラーを追跡しやすくなります。  
  
## 参照  
 [詳細な概念](../msbuild/msbuild-advanced-concepts.md)
---
title: "MSBuild エラー MSB3127 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.FileAssociationDefaultIconNotInstalled"
helpviewer_keywords: 
  - "MSB3127"
ms.assetid: 161eea9a-332f-463e-a49e-d4030e937d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3127
**MSB3127: 既定のアイコン \<iconname\> が現在のファイル参照で見つからないか、必要なダウンロード グループに含まれていません。  既定のアイコンのファイル名では大文字と小文字が区別されるため、アプリケーション マニフェストで参照されるファイル名は、アイコンのファイル名と完全に一致する必要があります。**  
  
 ファイルの関連付けを使用するように構成されているアプリケーションを発行する場合、マニフェストで参照される既定のアイコンは、現在のファイル参照内にあるか、必要なダウンロード グループに含まれている必要があります。  既定のアイコンは、ファイルの関連付けが構成されている \(ファイル名拡張子が構成されている\) ファイルに対して表示されるアイコンです。  
  
### このエラーを解決するには  
  
-   アイコン ファイルを現在のプロジェクトに追加し、必要なダウンロード グループに含めます。  詳細については、「[方法 : ClickOnce で発行されるファイルを指定する](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md)」を参照してください。  
  
## 参照  
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)
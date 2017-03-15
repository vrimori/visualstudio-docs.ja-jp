---
title: "MSBuild エラー MSB3172 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3172
**MSB3172: マニフェスト '\<ファイル\>' を読み取れません'  \<エラー\>'**  
  
 このエラーは、ビルド処理によるマニフェスト ファイルの読み取り中に一般的な問題が生じた場合に生成されます。  このエラー メッセージには、ファイル名に続いて、問題の詳細が示されます。  
  
 アセンブリまたはマニフェスト ファイルをコンテンツ ファイルとして追加した可能性があります。  依存アセンブリがプロジェクト システムで適切に参照されるように、**\[ファイルの追加\]** ではなく **\[参照の追加\]** コマンドを使用する必要があります。  通常、より高度なプロジェクトでは、bin フォルダー内の .exe.manifest がプロジェクト ファイルとしてマークされますが、このマークを回避する必要があります。  非表示の app.manifest ファイルは .exe.manifest ファイルになり、高度なシナリオに合わせて手動で編集できます。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)
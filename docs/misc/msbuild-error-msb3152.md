---
title: "MSBuild エラー MSB3152 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3152
**MSB3152: 必須コンポーネントのインストール場所が、'コンポーネントの開発元の Web サイト' に設定されていません。項目 '\<パッケージ\>' のファイル '\<ファイル\>' がディスクに見つかりません。  詳細については、ヘルプを参照してください。**  
  
 このエラーは、必須コンポーネントのインストーラーで必要なファイルが見つからない場合に発生します。  インストーラー ファイルは、再頒布可能パッケージ用に Visual Studio が予約済みの特別なフォルダーに格納されます。  このフォルダーは、開発に使用する Visual Studio のバージョンによって異なります。  特定のフォルダーの場所の詳細については、「[ブートストラップ パッケージの作成](../deployment/creating-bootstrapper-packages.md)」を参照してください。  
  
### このエラーを解決するには  
  
-   ファイルがディスク上に存在するかどうかを確認します。  
  
-   HomeSite を使用して、パッケージの問題の解決を図ります。  
  
-   プロジェクト ファイルで `CopyComponents` を `false` に設定します。  
  
-   壊れたブートストラップ パッケージを使用しないようにします。  
  
## 参照  
 [ブートストラップ パッケージの作成](../deployment/creating-bootstrapper-packages.md)
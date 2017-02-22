---
title: "ClickOnce がアプリケーションの更新を実行するしくみ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 配置, 更新"
  - "配置 (アプリケーションを) [ClickOnce], アプリケーションの更新プログラム"
  - "更新, ClickOnce"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce がアプリケーションの更新を実行するしくみ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce は、アプリケーションの配置マニフェストに指定されたファイル バージョン情報を使用して、アプリケーションのファイルを更新するかどうかを決定します。  更新が開始されると、ClickOnce は*ファイル パッチ*と呼ばれる技術を使用して、アプリケーション ファイルが重複してダウンロードされないようにします。  
  
## ファイル パッチ  
 ClickOnce は、アプリケーションを更新する際に、ファイルが変更されていない限り、新しいバージョンのアプリケーションに対応するすべてのファイルをダウンロードするわけではありません。  代わりに、現在のアプリケーションのアプリケーション マニフェストに指定されたファイルのハッシュ署名を、新しいバージョンのマニフェストに指定された署名と比較します。  ファイルの署名が異なっていれば、ClickOnce は新しいバージョンをダウンロードします。  署名が一致する場合、ファイルは元のバージョンから変更されていません。  この場合、ClickOnce は既存のファイルをコピーし、それを新しいバージョンのアプリケーションで使用します。  この手法により ClickOnce は、数ファイルのみが変更された場合にアプリケーション全体をダウンロードし直さなくても済むようにしています。  
  
 ファイル パッチは、必要に応じて <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> メソッドおよび <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> メソッドを使用してダウンロードされるアセンブリにも対応します。  
  
 Visual Studio を使用してアプリケーションをコンパイルした場合は、プロジェクト全体をビルドし直すたびに、すべてのファイルに対して新しいハッシュ署名が生成されます。  この状況では、数個のアセンブリのみが変更された場合でも、すべてのアセンブリがクライアントにダウンロードされます。  
  
 データとしてマークされ、データ ディレクトリに格納されているファイルには、ファイル パッチが機能しません。  これらのファイルは、そのハッシュ署名に関係なく常にダウンロードされます。  データ ディレクトリの詳細については、「[ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)」を参照してください。  
  
## 参照  
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)
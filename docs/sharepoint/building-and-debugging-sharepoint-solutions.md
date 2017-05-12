---
title: "SharePoint ソリューションのビルドとデバッグ"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, ビルドとデバッグ"
  - "Visual Studio での SharePoint 開発, デバッグ"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# SharePoint ソリューションのビルドとデバッグ
  一般に、SharePoint ソリューションのビルドとデバッグは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] における他の種類のプロジェクトのビルドとデバッグと同様です。  このセクションのトピックでは、わずかながら存在する相違点について説明します。  
  
## SharePoint ソリューションのプロジェクト出力  
 SharePoint ソリューションをビルドすると、アセンブリとソリューション パッケージ \(.wsp\) ファイルが作成されます。  これらのファイルのビルド時の場所を次の表に示します。  
  
|ビルド項目|出力フォルダー|  
|-----------|-------------|  
|アセンブリ ファイル、プログラム データベース \(PDB\) ファイル、および .wsp ファイル|*ProjectName*の\\bin\\debug または *ProjectName*の\\bin\\release|  
|SharePoint プロジェクト項目ファイル|*ProjectName*の\\pkg\\debug または *ProjectName*の\\pkg\\release|  
|ビルドの中間ファイル|*ProjectName*の\\obj\\debug または *ProjectName*の\\obj\\release|  
|パッケージの中間ファイル|*ProjectName*の\\pkgobj\\debug または *ProjectName*の\\pkgobj\\release|  
  
## SharePoint ソリューションのビルド  
 SharePoint ソリューションをビルドするには、開発用コンピューターに正しいバージョンの SharePoint サーバーがインストールされている必要があります。  それ以外については、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で他の種類のプロジェクトをビルドする場合と変わりません。  詳細については、「[方法: SharePoint ソリューションをビルドする](../sharepoint/how-to-build-sharepoint-solutions.md)」を参照してください。  
  
## SharePoint ソリューションのデバッグとテスト  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、デバッグの前に .wsp パッケージが SharePoint サーバーにコピーされ、サイトと Web スコープのフィーチャーがアクティブ化されて、場合によってはプロジェクトが開始されます。  また、プロジェクトを手動で開く必要があります。  詳細については、「[SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)」および「[SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)」を参照してください。  
  
## SharePoint Solutions を Using ALM Features でデバッグを確認します。  
 IntelliTrace と単体テストのような Visual Studio ALM 機能より正確に SharePoint ソリューションの正確な問題を解決する。  プロファイリングは、SharePoint ソリューションのパフォーマンスの問題点を特定し、識別できるようになります。  詳細については、「[SharePoint コードの検証およびデバッグ](../sharepoint/verifying-and-debugging-sharepoint-code.md)」および「[SharePoint アプリケーションのパフォーマンスのプロファイリング](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)」を参照してください。  
  
## ビルド処理中のセキュリティ  
 SharePoint ソリューションをパッケージ化したり配置したりするには、SharePoint サーバーにファイルをコピーするためのアクセス許可が [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] に必要です。  SharePoint サーバーのサイト コレクションの管理者であるユーザー アカウントを使用して、昇格されたプロセスとして [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を実行する必要があります。  また、プロジェクトがサンドボックス ソリューションかファーム ソリューションかを指定する必要もあります。  詳細については、「[サンドボックス ソリューションとファーム ソリューションの違い](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)」を参照してください。  
  
## \[消去\] コマンドの使用  
 デバッグのために SharePoint サーバーにインストールされた SharePoint ソリューションは、**\[クリーン\]** コマンドを実行してもアンインストールされません。  代わりに、SharePoint の構成でフィーチャーを非アクティブにする必要があります。  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [サーバー エクスプローラーを使用した SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
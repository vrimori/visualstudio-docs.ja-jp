---
title: "複数バージョンの Visual Studio のインストール | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "side-by-side インストール [Visual Studio]"
  - "ヘルプ [Visual Studio]、インストール"
  - "Express Edition [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 複数バージョンの Visual Studio のインストール
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio のこのバージョンは、旧バージョンの Visual Studio が既にインストールされたコンピューターにもインストールできます。 インストールに失敗した場合は、[ログ収集ツール](http://go.microsoft.com/fwlink/?LinkId=262077)を使用して失敗に関する情報を収集し、自分で問題をデバッグできます。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンをリリースされた順にインストールすることをお勧めします。 たとえば、Visual Studio 2015 をインストールする前に Visual Studio 2013 をインストールします。  
  
 複数のバージョンを並行してインストールする前に、次の条件を確認してください。  
  
-   Visual Studio 2015 を使用して [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] で作成されたソリューションを開くと、Visual Studio 2015 に固有の機能を実装しない限り、後で以前のバージョンのソリューションを開き、再度変更できます。  
  
-   Visual Studio 2015 を使用して [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 以前のバージョンで作成されたソリューションを開こうとすると、Visual Studio 2015 と互換性のあるプロジェクトとファイルの変更が必要になる場合があります。 詳細については、「[Visual Studio プロジェクトの移植、移行、およびアップグレード](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)」を参照してください。  
  
-   複数のバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がコンピューターにインストールされている場合、そのうちの 1 つのバージョンをアンインストールすると、すべてのバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のファイルの関連付けが削除されます。 ファイルの関連付けを再度割り当てるには、**\[オプション\]** ダイアログ ボックスの **\[環境\]**、**\[全般\]** ページにある [&#91;ファイルの関連付けを復元&#93;](../ide/reference/general-environment-options-dialog-box.md) を使用します。  
  
-   すべての拡張機能に互換性があるわけではないので、Visual Studio は拡張機能を自動的にアップグレードしません。[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=178891)またはソフトウェア発行者から入手した拡張機能を再インストールする必要があります。  
  
## .NET Framework のバージョンと複数バージョンのインストール  
  
-   Visual Basic、Visual C\#、および Visual F\# のプロジェクトでは、**プロジェクト デザイナー**の **\[ターゲット フレームワーク\]** オプションを使用して、プロジェクトで使用する .NET Framework のバージョンを指定します。 C\+\+ プロジェクトでは、.vcxproj ファイルを変更すると、ターゲット フレームワークを手動で変更できます。 詳細については、「[バージョンの互換性](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)」を参照してください。  
  
     プロジェクトを作成するときは、プロジェクトが対象とする .NET Framework のバージョンを **\[新しいプロジェクト\]** ダイアログ ボックスの **\[.NET Framework\]** の一覧で指定できます。  
  
     言語固有の情報については、次の表の適切なトピックを参照してください。  
  
    |言語|トピック|  
    |--------|----------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)|  
    |Visual C\#|[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Application%20Page,%20Project%20Designer%20\(C%23\).md)|  
    |Visual F\#|[Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../extensibility/debugger/includes/jsprjscript_md.md)]|[以前のバージョンの共通言語ランタイムでの JScript アプリケーションの実行](http://msdn.microsoft.com/ja-jp/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## 参照  
 [Visual Studio のインストール](../Topic/Installing%20Visual%20Studio%202015.md)   
 [Visual Studio プロジェクトの移植、移行、およびアップグレード](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [バージョンの互換性](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [複数言語バージョンの Visual Studio のインストール](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [C\/C\+\+ 分離アプリケーションおよび side\-by\-side アセンブリのビルド](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
---
title: "プロジェクトのアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage をアップグレードします。"
  - "戦略のアプリケーションのアップグレード"
  - "Vspackages にある、アップグレードのサポート"
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトのアップグレード
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の 1 種類のバージョンから次へのプロジェクト モデルへの変更は新しいバージョンで実行できるようにプロジェクトとソリューションをアップグレードする必要がある場合があります。  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] は独自のプロジェクトのアップグレードのサポートを実装するために使用できるインターフェイスが用意されています。  
  
## のアップグレード方法  
 アップグレードをサポートするにはプロジェクトのシステムの実装はアップグレード方法を定義および実装する必要があります。  方法の決定 \(SxS\) の side\-by\-side のバックアップバックアップ コピーまたはその両方をサポートできます。  
  
-   SxS のバックアップはプロジェクトのアップグレードが必要になる適切なファイル名のサフィックスを追加します \(たとえばそれらのファイルが 「 .old 」コピーされることを意味します。  
  
-   バックアップ コピーはプロジェクトがすべてのプロジェクト項目をユーザーが指定したバックアップの場所をコピーすることを意味します。  元のプロジェクトの場所の関連ファイルはアップグレードされます。  
  
## アップグレードのしくみ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の旧バージョンで作成されたソリューションが新しいバージョンで開くとIDE にアップグレードする必要があるかどうかを判断するためにソリューション ファイルをチェック アウトします。  アップグレードが必要な場合は **アップグレード ウィザード**  はアップグレード プロセスを解説しているユーザーは自動的に起動します。  
  
 ソリューションをアップグレードする必要がある場合はアップグレードの方法の各プロジェクト ファクトリを呼び出します。  ファクトリの方法はプロジェクトのバックアップ コピーまたは SxS のバックアップをサポートするかどうかを判定します。  バックアップに必要な情報を収集しユーザーに適切なオプションを示す情報は  **アップグレード ウィザード**  に渡されます。  
  
### 複数のプロジェクトから成るソリューション  
 ソリューションに複数のプロジェクトが含まれている場合はアップグレードの方法が異なる場合などの SxS のバックアップおよび Web プロジェクトだけをサポートするバックアップ コピーのみをサポートする C\+\+. C\+\+ プロジェクトはプロジェクト ファクトリのアップグレード方法を調整する必要があります。  
  
 ソリューションは <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> の各プロジェクト ファクトリを呼び出します。  次にグローバルなプロジェクト ファイルが確認アップグレードする必要があるサポートされるアップグレード方法を呼び出しますかどうかを確認するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> を示します。   **アップグレード ウィザード**  によって呼び出されます。  
  
 ユーザーがウィザードを完了すると<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> は実際のアップグレードを実行する各プロジェクト ファクトリ呼び出されます。  バックアップを簡単にするためにIVsProjectUpgradeViaFactory のメソッドはアップグレード プロセスの詳細を記録するように <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> サービスを提供します。  このサービスはキャッシュすることはできません。  
  
 関連するすべてのグローバル ファイルを更新したらプロジェクトをインスタンス化するには各プロジェクト ファクトリを選択できます。  実現はプロジェクト <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> をサポートする必要があります。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> のメソッドは関連するすべてのプロジェクト項目をアップグレードするために呼び出されます。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> のメソッドは SVsUpgradeLogger サービスを提供しません。  このサービスは <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> を呼び出して取得できます。  
  
## ベスト プラクティス  
 使用できる編集し保存するにはファイルを編集する前にファイルを保存できる確認するにはサービスを <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>。  これはバックアップができ実装をアップグレードするソース管理下のプロジェクト ファイル適切なアクセス許可がないファイルなどを処理します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> サービスのバックアップのすべてのフェーズ中に使用するアップグレード プロセスの成功または失敗に関する情報を提供するようにアップグレードします。  
  
 プロジェクトをバックアップしアップグレードする方法の詳細についてはvsshell2.idl の IVsProjectUpgrade についてはコメントを参照してください。  
  
## 参照  
 [プロジェクト](../../extensibility/internals/projects.md)   
 [カスタム プロジェクトのアップグレード](../../misc/upgrading-custom-projects.md)   
 [プロジェクト項目のアップグレード](../../misc/upgrading-project-items.md)
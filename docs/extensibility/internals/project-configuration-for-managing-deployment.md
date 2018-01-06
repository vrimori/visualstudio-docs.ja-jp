---
title: "プロジェクトの展開を管理するための構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4859e47f8a7ade34a920e4d8e2fac3be58508de3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-managing-deployment"></a>展開を管理するためのプロジェクトの構成
展開は、動作は、デバッグおよびインストールの予期される場所に、ビルド プロセスからの出力項目を物理的に移動します。 たとえば、Web アプリケーションをローカル コンピューター上に構築され、サーバー上に配置しする可能性があります。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトを配置に影響すること、2 つの方法をサポートします。  
  
-   として、展開プロセスの件名です。  
  
-   展開プロセスのマネージャーです。  
  
 ソリューションを展開する前にまず展開オプションを構成するデプロイ プロジェクトを追加する必要があります。 プロジェクトの配置が既に存在しない場合を選択すると、1 つを作成するかどうかは寄せられるは**ソリューションの配置**から、**ビルド**メニューかソリューションを右クリックします。 クリックすると**はい**が表示されます、**新しいプロジェクトの追加** ダイアログ ボックスで、**リモートの展開ウィザード**プロジェクトを選択します。  
  
 リモートの展開ウィザードでは、アプリケーション (Windows または Web) の種類、含めるプロジェクト出力グループ、すべて追加ファイルを含めるには、およびリモート コンピューターに展開するが求められます。 ウィザードの最後のページには、選択したオプションの概要が表示されます。  
  
 展開プロセスの対象となるプロジェクトでは、代替の環境に移動する必要があります出力項目を生成します。 これらの出力項目の説明をパラメーターとして、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>インターフェイスを持つプライマリ目的のグループの出力にプロジェクトを許可する場合。 実装に関連する詳細については`IVsProjectCfg2`を参照してください[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)です。  
  
 配置プロジェクトは、展開プロセスを管理するは、[配置] コマンドを有効にし、このコマンドが選択されている場合に対応します。 デプロイ プロジェクトの実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 、展開を実行して、呼び出しを行うのためのインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>レポートへのインターフェイスは、ステータス イベントを展開します。  
  
 構成は、ビルドまたは配置の動作に影響する依存関係を指定できます。 ビルドまたは配置の依存関係が必要がありますか、ビルドまたは自体の構成をビルドまたは配置される後または前に配置するプロジェクトです。 プロジェクト間でのビルドの依存関係がで説明されている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>インターフェイスし、の依存関係を配置、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>インターフェイスです。 詳細については、次を参照してください。[構築するためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)です。  
  
## <a name="see-also"></a>参照  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [出力のためのプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)
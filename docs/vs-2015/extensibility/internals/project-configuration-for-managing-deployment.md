---
title: プロジェクトの展開を管理するための構成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6ea732449c92b2dffb91c7e90ff738791b7c2f7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721365"
---
# <a name="project-configuration-for-managing-deployment"></a>展開の管理のためのプロジェクト構成
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

展開は、デバッグ、およびインストールの予期される場所に、ビルド プロセスからの出力項目を物理的に移動するのです。 たとえば、Web アプリケーションをローカル コンピューター上に構築され、サーバー上に配置しする可能性があります。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] サポートを投影する 2 つの方法は、展開にかかわることができます。  
  
- 展開プロセスの対象。  
  
- 展開プロセスのマネージャー。  
  
  ソリューションを展開する前にまず、展開オプションを構成する展開プロジェクトを追加する必要があります。 デプロイ プロジェクトが存在しない場合かどうかは、1 つを選択すると、作成するよく寄せられる、**ソリューションの配置**から、**ビルド**メニューか、ソリューションを右クリックします。 クリックすると**はい**が表示されます、**新しいプロジェクトの追加** ダイアログ ボックスで、**リモートの展開ウィザード**プロジェクトを選択します。  
  
  リモートの展開ウィザードでは、(Windows または Web) アプリケーションの種類、プロジェクト出力グループに含める、追加のファイルに含める、およびリモート コンピューターに配置するが表示されます。 ウィザードの最後のページは、選択したオプションの概要を表示します。  
  
  展開プロセスの対象となるプロジェクトは、別の環境に移動する必要があります出力項目を生成します。 これらの出力パラメーターとして項目が説明されている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>がプライマリ プロジェクト出力のグループに許可する場合の目的のインターフェイス。 実装に関する詳細情報の`IVsProjectCfg2`を参照してください[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)します。  
  
  展開プロジェクトは、展開プロセスを管理するは、展開コマンドを有効にし、このコマンドが選択されているときに応答します。 配置プロジェクトの実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>配置を実行し、呼び出しを行うのためのインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>レポートへのインターフェイスは、ステータス イベントを展開します。  
  
  構成は、ビルドまたは配置の動作に影響する依存関係を指定できます。 ビルドまたは配置する必要がありますか、ビルドまたは配置前に、または後、構成自体をビルドまたは配置されるプロジェクト依存関係とは。 プロジェクト間でのビルド依存関係と共に説明しています、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>インターフェイスし、依存関係をデプロイ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>インターフェイス。 詳細については、次を参照してください。[構築するためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)します。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [ビルドするためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)   
 [出力のためのプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)


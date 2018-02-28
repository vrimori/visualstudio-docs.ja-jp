---
title: "ソリューションの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 539ceb45cce6c317ed3723c5006e6d2a77029335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="solutions-overview"></a>ソリューションの概要
ソリューションは、連携するアプリケーションを作成する 1 つまたは複数のプロジェクトのグループです。 ソリューションに関連するプロジェクトとステータスの詳細については、2 つの別のソリューション ファイルに格納されます。 ソリューション (.sln) ファイルはテキスト ベースしソース コード管理下に配置およびユーザーの間で共有できます。 ソリューション ユーザー オプション (.suo) ファイルはバイナリです。 その結果、.suo ファイルはソース コード管理下に配置することはできませんし、ユーザーに固有の情報が含まれています。  
  
 任意の VSPackage は、ソリューション ファイルのいずれかの型を記述できます。 ファイルの性質上、書き込みを行うために実装する 2 つの異なるインターフェイスがあります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>インターフェイスでは、テキストの情報が、.sln ファイルに書き込まれますと<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>インターフェイス .suo ファイルをバイナリ ストリームに書き込みます。  
  
> [!NOTE]
>  プロジェクトは自身のソリューション ファイルにエントリを明示的に記述する必要はありません。環境では、プロジェクトのことを処理します。 したがって、ソリューション ファイルを具体的には追加のコンテンツを追加する場合を除き、この方法で、VSPackage を登録する必要はありません。  
  
 ソリューションの永続化をサポートする VSPackage ごと、3 つのインターフェイスを使用する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 、環境で実装されると、VSPackage によってと呼ばれる、インターフェイスと`IVsPersistSolutionProps`と`IVsPersistSolutionOpts`、いずれも、実装は、VSPackage によってです。 `IVsPersistSolutionOpts`のみインターフェイスを秘密情報が、VSPackage によって .suo ファイルに書き込まれる場合に実装する必要があります。  
  
 ソリューションを開いたときに、次のプロセスが行われます。  
  
1.  環境では、ソリューションを読み取ります。  
  
2.  環境が検出されると、 `CLSID`、対応する VSPackage が読み込まれます。  
  
3.  かどうか、VSPackage が読み込まれると、環境呼び出し`QueryInterface`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>インターフェイスの VSPackage を必要とするためのインターフェイスです。  
  
    1.  .Sln ファイルから読み取る場合、環境が呼び出す`QueryInterface`の`IVsPersistSolutionProps`します。  
  
    2.  .Suo ファイルから読み取る場合、環境が呼び出す`QueryInterface`の`IVsPersistSolutionOpts`します。  
  
 これらのファイルの使用に関連する特定の情報は含まれて[ソリューション (です。Sln) ファイル](../../extensibility/internals/solution-dot-sln-file.md)と[ソリューション ユーザー オプション (です。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)です。  
  
> [!NOTE]
>  2 つのプロジェクトの構成で構成されると、ビルドからの 3 つ目の除外は、新しいソリューション構成を作成する場合は、プロパティ ページの UI またはオートメーションを使用する必要があります。 ソリューションのビルド マネージャーの構成とそのプロパティを直接変更することはできませんを使用して、ソリューションのビルド マネージャーを操作することができます、 `SolutionBuild` dte オートメーション モデル内のクラスです。 ソリューションを構成する方法の詳細については、次を参照してください。[ソリューション構成](../../extensibility/internals/solution-configuration.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
---
title: ソリューションの概要 |Microsoft Docs
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
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d9eb36da433575710ae7f24da85e4a1a0970b79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781063"
---
# <a name="solutions-overview"></a>ソリューションの概要
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソリューションは、連携してアプリケーションを作成する 1 つまたは複数のプロジェクトのグループです。 ソリューションに関連するプロジェクトとステータス情報は、2 つの別のソリューション ファイルに格納されます。 ソリューション (.sln) ファイルはテキスト ベースおよびソース コード管理下に置くし、ユーザーの間で共有できます。 ソリューション ユーザー オプション (.suo) ファイルはバイナリです。 その結果、.suo ファイルは、ソース コード管理下に置くことはできませんし、ユーザー固有の情報が含まれています。  
  
 すべての VSPackage は、ソリューション ファイルのいずれかの型を記述できます。 ファイルの性質上、書き込みを禁止するために実装する 2 つの異なるインターフェイスがあります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>インターフェイスが .sln ファイルにテキスト情報を書き込みます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>インターフェイスは、.suo ファイルをバイナリ ストリームを書き込みます。  
  
> [!NOTE]
>  プロジェクトは自身のソリューション ファイルにエントリを明示的に記述する必要はありません。環境では、プロジェクトを処理します。 そのため、ソリューション ファイルを具体的には追加のコンテンツを追加する場合を除き、この方法で、VSPackage を登録する必要はありません。  
  
 ソリューションの永続化をサポートしている各 VSPackage が 3 つのインターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>インターフェイスは、環境によって実装され、VSPackage によって呼び出されると`IVsPersistSolutionProps`と`IVsPersistSolutionOpts`VSPackage ではいずれも実装します。 `IVsPersistSolutionOpts`のみインターフェイスを秘密情報を VSPackage によって .suo ファイルに書き込まれる場合に実装する必要があります。  
  
 ソリューションが開かれたときに、次のプロセスが行われます。  
  
1. 環境では、ソリューションを読み取ります。  
  
2. 環境が検出されると、 `CLSID`、対応する VSPackage が読み込まれます。  
  
3. かどうか、VSPackage が読み込まれる、環境は`QueryInterface`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>VSPackage を必要とするインターフェイスのインターフェイス。  
  
   1.  .Sln ファイルから読み取る場合、環境を呼び出す`QueryInterface`の`IVsPersistSolutionProps`します。  
  
   2.  環境が呼び出す、.suo ファイルから読み取る場合、`QueryInterface`の`IVsPersistSolutionOpts`します。  
  
   これらのファイルの使用に関連する特定の情報が記載されて[ソリューション (します。Sln) ファイル](../../extensibility/internals/solution-dot-sln-file.md)と[ソリューション ユーザー オプション (します。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)します。  
  
> [!NOTE]
>  新しいソリューション構成の 2 つのプロジェクト構成で構成されると、ビルドからの 3 つ目の除外を作成する場合は、プロパティ ページの UI またはオートメーションを使用する必要があります。 ソリューションのビルド マネージャーの構成とそのプロパティを直接変更することはできませんを使用して、ソリューションのビルド マネージャーを操作することができます、 `SolutionBuild` DTE からオートメーション モデルのクラス。 ソリューションを構成する方法の詳細については、次を参照してください。[ソリューション構成](../../extensibility/internals/solution-configuration.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>


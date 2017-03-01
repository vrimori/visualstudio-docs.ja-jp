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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 06ca562112b8b6feb711219502e3d10b1cb6f462
ms.lasthandoff: 02/22/2017

---
# <a name="solutions-overview"></a>ソリューションの概要
ソリューションは、連携してアプリケーションを作成する&1; つまたは複数のプロジェクトのグループです。 ソリューションに関連するプロジェクトとステータス情報は、2 つの別のソリューション ファイルに格納されます。 ソリューション (.sln) ファイルはテキスト ベースおよびソース コード管理下に配置され、ユーザー間で共有されることができます。 ソリューション ユーザー オプション (.suo) ファイルはバイナリです。 この結果、.suo ファイルでは、ソース コード管理下に配置することはできませんし、ユーザーに固有の情報が含まれています。  
  
 すべての VSPackage は、ソリューション ファイルのいずれかの型を記述できます。 ファイルであるのため、書き込みを禁止するために実装する&2; つの異なるインターフェイスがあります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>インターフェイスは、.sln ファイルをテキストの情報を書き込みますと<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>インターフェイスは、.suo ファイルをバイナリ ストリームを書き込みます</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>。  
  
> [!NOTE]
>  プロジェクトがそれ自体のため、ソリューション ファイルにエントリを明示的に記述する必要はありません。環境では、プロジェクトのことを処理します。 そのため、ソリューション ファイルに具体的には追加のコンテンツを追加する場合を除き、この方法で、VSPackage を登録する必要はありません。  
  
 ソリューションの永続化をサポートする各 VSPackage が&3; つのインターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>インターフェイスは、環境によって実装され、VSPackage によって呼び出されると`IVsPersistSolutionProps`と`IVsPersistSolutionOpts`VSPackage ではどちらも実装します</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。 `IVsPersistSolutionOpts`のみインターフェイスを秘密情報を VSPackage .suo ファイルに書き込む場合に実装する必要があります。  
  
 ソリューションを開いたときに、次のプロセスが行われます。  
  
1.  環境では、ソリューションを読み込みます。  
  
2.  環境が検出されると、 `CLSID`、対応する VSPackage が読み込まれます。  
  
3.  VSPackage が読み込まれます、環境の呼び出し`QueryInterface`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>VSPackage を要求するインターフェイスのインターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。  
  
    1.  .Sln ファイルから読み取る場合、環境を呼び出します`QueryInterface`の`IVsPersistSolutionProps`です。  
  
    2.  .Suo ファイルから読み取る場合、環境を呼び出します`QueryInterface`の`IVsPersistSolutionOpts`です。  
  
 これらのファイルの使用に関連する特定の情報は記載されて[ソリューション (します。Sln) ファイルに](../../extensibility/internals/solution-dot-sln-file.md)と[ソリューション ユーザー オプション (します。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)します。  
  
> [!NOTE]
>  2 つのプロジェクト構成で構成されると、ビルドからの&3; つ目の除外は、新しいソリューション構成を作成する場合は、プロパティ ページの UI またはオートメーションを使用する必要があります。 ソリューションのビルド マネージャーの構成とそのプロパティを直接変更することはできませんを使用して、ソリューションのビルド マネージャーを操作できる、 `SolutionBuild` dte オートメーション モデル内のクラスです。 ソリューションを構成する方法の詳細については、次を参照してください。[ソリューション構成](../../extensibility/internals/solution-configuration.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

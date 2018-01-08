---
title: "その他のファイル プロジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d3fa64b06504d8982594945f5b0c38956676b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="miscellaneous-files-project"></a>その他のファイル プロジェクト
ユーザーは、プロジェクト項目を開く、IDE は、ソリューション内のすべてのプロジェクトのメンバーではないすべての項目をその他のファイル プロジェクトに割り当てます。  
  
 プロジェクトでは、どのエディターを使用して、ユーザーがプロジェクト項目を開くときに決定する重要な役割を果たします。 プロジェクトを設計すると、プロジェクト固有のエディターまたは標準のエディターを使用して特定のファイルを開きます。  
  
 プロジェクト固有のエディターは、通常、ユーザーが特別な知識があること、またはプロジェクトからの特別なインターフェイスを使用する必要があります。 詳細については、次を参照してください。[する方法: 開いているプロジェクトに固有のエディター](../../extensibility/how-to-open-project-specific-editors.md)です。  
  
 標準のエディターでは、すべてのプロジェクトで特定の拡張機能の任意のファイルを開くことができます。 ユーザーになど、一部の標準的なエディターをカスタマイズする、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクト用のテキスト エディターが、まだ、パブリックの文字を保持します。 標準のエディターを使用して作成される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドです。  
  
 ソリューション内のプロジェクトが応答しないためのプロジェクト項目を開くことができますが、IDE は、ファイルを開くその他のファイル プロジェクトという特殊なプロジェクトを提供します。  
  
 この特殊なプロジェクトは、プロジェクトのコンテキストの外部ファイルのオープンを提供します。 処理中に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>メソッド、その他のファイル プロジェクトの応答が非常に低い優先順位。 そのため、その他のファイルはプロジェクト ファイルを開くことができる任意の優先順位の高いプロジェクトに生成では常にします。  
  
 その他のファイル プロジェクトには、ユーザーを明示的に作成では不要、**新しいプロジェクト** ダイアログ ボックス。 また、その他のファイル プロジェクトはプロジェクトのメンバーの一覧を完全に管理しません。 省略可能な機能を使用して各ユーザーの最近使用したファイルの一覧を記録します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [プロジェクト テンプレートとプロジェクト項目テンプレートの追加](../../extensibility/internals/adding-project-and-project-item-templates.md)
---
title: その他のファイル プロジェクト |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4305b5a65ee8303fa98cc3a25202fe1fca38e571
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923767"
---
# <a name="miscellaneous-files-project"></a>その他のファイル プロジェクト
ユーザーは、プロジェクト項目が開いたら、IDE はソリューション内のすべてのプロジェクトのメンバーではないすべての項目をその他のファイル プロジェクトに割り当てます。  
  
 プロジェクトでは、どのエディターを使用するは、ユーザーがプロジェクト項目を開いたときに決定する際の重要な役割を果たします。 プロジェクトを設計すると、プロジェクト固有のエディターまたは標準のエディターを使用して特定のファイルを開きます。  
  
 プロジェクト固有のエディターは、通常、ユーザーが特別な知識があるか、プロジェクトからの特別なインターフェイスを使用する必要があります。 詳細については、「[方法 :プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)します。  
  
 標準エディターでは、すべてのプロジェクトで特定の拡張機能の任意のファイルを開くことができます。 ユーザーがなど、一部の標準エディターをカスタマイズすることができます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクト用のテキスト エディターは、パブリックの文字を保持します。 標準のエディターを使用して作成された、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッド。  
  
 ソリューション内のプロジェクトが返されないプロジェクト項目を開くことができますが、IDE は、任意のファイルを開き、その他のファイル プロジェクトと呼ばれる特別なプロジェクトを提供します。  
  
 この特別なプロジェクトは、プロジェクトのコンテキストの外部のファイルを開くのために提供します。 処理中に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>メソッド、その他のファイル プロジェクトは常に非常に低い優先順位が応答します。 そのため、その他のファイルはプロジェクト ファイルを開くことができる任意の優先順位の高いプロジェクトに生成では常にします。  
  
 その他のファイル プロジェクトには、それを明示的に作成するユーザーは不要、**新しいプロジェクト** ダイアログ ボックス。 また、その他のファイル プロジェクトはプロジェクトのメンバーの一覧を完全に管理しません。 各ユーザーの最近使用したファイルの一覧を記録するのにオプションの機能を使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [方法: 開いているプロジェクト固有のエディター](../../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [プロジェクト テンプレートとプロジェクト項目テンプレートの追加](../../extensibility/internals/adding-project-and-project-item-templates.md)
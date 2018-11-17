---
title: プロジェクトの優先順位 |Microsoft Docs
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
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d052658cc6f61027def4fdae89c2981581b7e27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742323"
---
# <a name="project-priority"></a>プロジェクトの優先順位
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクト項目は、通常、ソリューション内の 1 つしかプロジェクトのメンバーです。 そのため、IDE 簡単に判断できますプロジェクトは、項目を開くために使用します。 ただし、項目が 1 つ以上のプロジェクトのメンバーである場合は、IDE は、項目を開くための最適なプロジェクトを決定する優先度スキームを使用します。  
  
 次に、プロジェクトの優先度スキームを示します。  
  
-   IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>ドキュメントがそのプロジェクトのメンバーであるかどうかを判断するソリューション内の各プロジェクトのメソッド。  
  
-   ドキュメントが、プロジェクトのメンバーである場合は、プロジェクトは応答優先度の割り当てがそのドキュメントの処理に従ってします。 たとえば、言語プロジェクトはその言語のソース ファイルの優先度の高い応答しますが、ビルド プロセスの一部として使用されていない、認識されないファイルの種類の優先順位の低い応答します。  
  
-   ドキュメントのカスタムのプロジェクトに固有のエディターまたはデザイナーを提供するプロジェクトでは、優先度の高いも受信します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙体は、ドキュメントの優先度の値を提供します。  
  
-   最高の優先順位を指定するプロジェクトには、文書を開くためのコンテキストが与えられます。 2 つのプロジェクトが同じ優先順位の値を返す場合、アクティブなプロジェクトをお勧めします。 ソリューション内のプロジェクトが返されない、ドキュメントを開くことができますが、その他のファイル プロジェクトにドキュメントが挿入されます。 詳細については、次を参照してください。 [Miscellaneous Files プロジェクト](../../extensibility/internals/miscellaneous-files-project.md)します。  
  
## <a name="see-also"></a>関連項目  
 [その他のファイル プロジェクト](../../extensibility/internals/miscellaneous-files-project.md)   
 [方法: 開いているドキュメントのエディターを開く](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [プロジェクト テンプレートとプロジェクト項目テンプレートの追加](../../extensibility/internals/adding-project-and-project-item-templates.md)


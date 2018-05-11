---
title: プロジェクトの優先度 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27341f78fb17fa5346a9dfbc7cdd3f86439d3d23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="project-priority"></a>プロジェクトの優先度
プロジェクト項目は、通常、ソリューション内の 1 つだけのプロジェクトのメンバーです。 そのため、IDE を容易に判別するプロジェクトを使用して、項目を開きます。 ただし、項目が 1 つ以上のプロジェクトのメンバーである場合は、IDE は、最適なプロジェクトの項目を開くことを確認するに優先順位スキームを使用しています。  
  
 次に、プロジェクトの優先順位のスキームを示します。  
  
-   IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>ドキュメントがそのプロジェクトのメンバーであるかどうかを確認するようにソリューション内の各プロジェクトのメソッドです。  
  
-   このドキュメントは、プロジェクトのメンバーは、プロジェクトを応答優先度の割り当てがそのドキュメントの処理に従ってします。 たとえば、言語プロジェクトその言語のソース ファイルの優先度の高い応答応答しますが、そのビルド プロセスの一部として使用されていない、認識されないファイルの種類の優先度の低い。  
  
-   ドキュメントのプロジェクト固有のカスタム エディターやデザイナーを提供するプロジェクトでは、優先度の高いも表示されます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙は、ドキュメントの優先順位の値を提供します。  
  
-   最高の優先順位を指定するプロジェクトには、ドキュメントを開くコンテキストが割り当てられます。 2 つのプロジェクトは同じ優先順位の値を返す場合、アクティブなプロジェクトをお勧めします。 ソリューション内のプロジェクトが返されない、ドキュメントを開くことができますが、その他のファイル プロジェクトにドキュメントが挿入されます。 詳細については、次を参照してください。 [Miscellaneous Files プロジェクト](../../extensibility/internals/miscellaneous-files-project.md)です。  
  
## <a name="see-also"></a>関連項目  
 [その他のファイル プロジェクト](../../extensibility/internals/miscellaneous-files-project.md)   
 [方法: 開いているドキュメントのエディターを開く](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [プロジェクト テンプレートとプロジェクト項目テンプレートの追加](../../extensibility/internals/adding-project-and-project-item-templates.md)
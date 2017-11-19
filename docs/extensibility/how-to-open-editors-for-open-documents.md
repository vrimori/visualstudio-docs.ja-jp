---
title: "方法: 開いているドキュメントに対して開いているエディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dfd145281a467a23cd01d73ff04721d68580254e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-editors-for-open-documents"></a>方法: 開いているドキュメントのエディターを開く
プロジェクトには、ドキュメント ウィンドウが開き、プロジェクト最初判断しなければなりませんかどうか、ファイルが既に開いているドキュメント ウィンドウには、別のエディター。 登録されている標準エディターのいずれかのプロジェクト固有のエディターで開くかなどがあります、または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="opening-a-project-specific-editor"></a>プロジェクトに固有のエディターを開く  
 次の手順を使用して、既に開いているファイルのプロジェクト固有のエディターを開きます。  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>開くには、開いているファイルをプロジェクトに固有のエディター  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> メソッドを呼び出します。  
  
     この呼び出しは、該当する場合に、ドキュメントの階層、階層アイテム、およびウィンドウ フレーム ポインターを返します。  
  
2.  ドキュメントが開いている場合は、プロジェクトがドキュメントのデータ オブジェクトのみが存在するかどうか、またはドキュメント ビュー オブジェクトが存在を確認する必要があります。  
  
    -   ドキュメント ビュー オブジェクトが存在し、このビューは、別の階層または階層アイテムのプロジェクトは、ビューのウィンドウ フレームへのポインターを使用して、既存のウィンドウを再び表面化します。  
  
    -   ドキュメント ビュー オブジェクトが存在し、このビューは、同じ階層および階層の項目には、プロジェクトは場合は、基になるドキュメント データ オブジェクトにアタッチできますが、2 つ目のビューを開くことができます。 それ以外の場合、プロジェクトでは、既存のウィンドウを再び表面化するビューのウィンドウ フレームへのポインターを使用する必要があります。  
  
    -   ドキュメント データ オブジェクトが存在する場合のみ、プロジェクトがドキュメント データ オブジェクトのビューに使用できるかどうかを決定する必要があります。 ドキュメント データ オブジェクトが互換性のある場合は、完了手順で説明した[プロジェクト固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md)です。  
  
     ドキュメント データ オブジェクトに互換性がない場合、エラーが示すファイルが現在使用中であることをユーザーに表示する必要があります。 このエラーだけを表示する一時的な場合は、ユーザーが以外のエディターを使用して、ファイルを開くしようとしているファイルが同時にコンパイルされるときなど、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア テキスト エディター。 コアのテキスト エディターでは、コンパイラで、ドキュメント データ オブジェクトを共有できます。  
  
3.  ドキュメント データ オブジェクト、またはドキュメント ビュー オブジェクトがないために、ドキュメントが開いていない場合は、手順を完了[プロジェクト固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md)です。  
  
## <a name="opening-a-standard-editor"></a>標準のエディターを開く  
 既にされているファイルの標準のエディターを開くには、次の手順を使用してを開きます。  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>開いているファイルの標準のエディターを開く  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> を呼び出す。  
  
     このメソッドは、ドキュメントがまだ開いていないを呼び出してことを確認最初<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>です。 ドキュメントが既に開いている場合は、そのエディター ウィンドウが示されます。  
  
2.  ドキュメントが開いていない場合は、手順を実行し、[する方法: 標準のエディターを開く](../extensibility/how-to-open-standard-editors.md)です。  
  
## <a name="see-also"></a>関連項目  
 [開くと、プロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: プロジェクトに固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../extensibility/how-to-open-standard-editors.md)
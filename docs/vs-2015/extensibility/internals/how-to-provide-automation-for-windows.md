---
title: '方法: Windows のオートメーションの提供 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6fad49e2841186cea677a165bdb48c4a1af5b41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539349"
---
# <a name="how-to-provide-automation-for-windows"></a>方法: Windows のオートメーションの提供
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: Windows のオートメーションの提供](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-automation-for-windows)します。  
  
ドキュメントとツール ウィンドウのための自動化を行うことができます。 オートメーション オブジェクトをウィンドウで使用できるようにして、環境が存在しないときに、オートメーションが勧めを提供するタスクの一覧は、既製のオートメーション オブジェクトを提供します。  
  
## <a name="automation-for-tool-windows"></a>ツールの Windows のオートメーション  
 環境の標準を返すことでツール ウィンドウでオートメーションを提供します<xref:EnvDTE.Window>次の手順で説明したようにオブジェクトします。  
  
#### <a name="to-provide-automation-for-tool-windows"></a>自動化ツール windows 用に提供するには  
  
1.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>で環境を使用してメソッド<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>として`VSFPROPID`を取得するパラメーター、`Window`オブジェクト。  
  
2.  呼び出し元が、ツール ウィンドウの VSPackage に固有のオートメーション オブジェクトを要求したとき<xref:EnvDTE.Window.Object%2A>、環境は`QueryInterface`の`IExtensibleObject`、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>、または`IDispatch`インターフェイス。 両方`IExtensibleObject`と`IVsExtensibleObject`提供、<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>メソッド。  
  
3.  環境を呼び出すと、`GetAutomationObject`メソッド`NULL`、バックアップ、VSPackage に固有のオブジェクトを渡すことによって応答します。  
  
4.  呼び出す場合`QueryInterface`の`IExtensibleObject`と`IVsExtensibleObject`環境を呼び出しますが、失敗した`QueryInterface`の`IDispatch`します。  
  
## <a name="automation-for-document-windows"></a>Windows のドキュメントのための自動化  
 標準的な<xref:EnvDTE.Document>オブジェクトは、エディターは、独自の実装を持つことができますが、環境からも、`T:EnvDTE.Document`実装することによってオブジェクト`IExtensibleObject`インターフェイスに応答して`GetAutomationObject`します。  
  
 さらに、エディターを使用して取得、VSPackage に固有のオートメーション オブジェクトを提供できます、<xref:EnvDTE.Document.Object%2A>メソッドを実装することによって、`IVsExtensibleObject`または`IExtensibleObject`インターフェイス。 [VSSDK のサンプル](../../misc/vssdk-samples.md)RTF ドキュメントに固有のオートメーション オブジェクトを提供します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>


---
title: '方法: Windows の自動化機能を提供 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c37123eeba42630b4b899966f7f4b0dc8c046fe8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-automation-for-windows"></a>方法: Windows 用のオートメーションの提供
ドキュメントとツール ウィンドウのオートメーションを使用できます。 オートメーションは適切では、ウィンドウのオートメーション オブジェクトを使用できるようにして、環境が存在しないときに提供することは、タスク一覧で、既製のオートメーション オブジェクトを提供します。

## <a name="automation-for-tool-windows"></a>ツール ウィンドウのオートメーション
 環境については、オートメーション ツール ウィンドウ、標準的なを返すことによって<xref:EnvDTE.Window>オブジェクトのように、次の手順で説明します。

#### <a name="to-provide-automation-for-tool-windows"></a>ツール ウィンドウのための自動化を提供するには

1.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>環境を使用して方法<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>として`VSFPROPID`を取得するパラメーター、`Window`オブジェクト。

2.  呼び出し元が、ツール ウィンドウの VSPackage に固有のオートメーション オブジェクトを要求したとき<xref:EnvDTE.Window.Object%2A>、環境の呼び出し`QueryInterface`の`IExtensibleObject`、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>、または`IDispatch`インターフェイスです。 両方`IExtensibleObject`と`IVsExtensibleObject`提供、<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>メソッドです。

3.  環境を呼び出すと、`GetAutomationObject`メソッド`NULL`、渡すことによって、応答は、VSPackage に固有のオブジェクトをバックアップします。

4.  呼び出す場合`QueryInterface`の`IExtensibleObject`と`IVsExtensibleObject`失敗した場合、環境が呼び出します`QueryInterface`の`IDispatch`します。

## <a name="automation-for-document-windows"></a>ドキュメント ウィンドウのための自動化
 標準的な<xref:EnvDTE.Document>オブジェクトは、エディターは、独自の実装を持つことができますが、環境からも、<xref:EnvDTE.Document>実装することによってオブジェクト`IExtensibleObject`インターフェイスに応答して`GetAutomationObject`です。

 さらに、エディターが使用して取得、VSPackage に固有のオートメーション オブジェクトを提供できます、<xref:EnvDTE.Document.Object%2A>メソッドを実装することによって、`IVsExtensibleObject`または`IExtensibleObject`インターフェイスです。 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)RTF ドキュメント固有のオートメーション オブジェクトを提供します。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
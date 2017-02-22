---
title: "方法: Windows 用の自動化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "オートメーション [Visual Studio SDK] ツール ウィンドウ"
  - "オートメーションのツール ウィンドウ"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: Windows 用の自動化
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ドキュメント ウィンドウとツール ウィンドウにオートメーションを指定できます。  オートメーションを指定するとタスク一覧とするようにウィンドウでオートメーション オブジェクトを使用できるようにする環境は既製のオートメーション オブジェクトを提供するたびに勧められ。  
  
## ツール ウィンドウのオートメーション  
 環境はツール ウィンドウで次の手順で説明するように <xref:EnvDTE.Window> の標準のオブジェクトを返すことによってオートメーションを提供します :  
  
#### オートメーションのツール ウィンドウに提供します。  
  
1.  `Window` のオブジェクトを取得するに `VSFPROPID` のパラメーターとして <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> の環境で <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> のメソッドを呼び出します。  
  
2.  呼び出し元が <xref:EnvDTE.Window.Object%2A> でツール ウィンドウに VSPackage 固有のオートメーション オブジェクトが要求されると環境は `IExtensibleObject`<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>または `IDispatch` インターフェイスの `QueryInterface` を呼び出します。  `IExtensibleObject` と `IVsExtensibleObject` は<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> のメソッドを提供します。  
  
3.  環境は`NULL` を渡す `GetAutomationObject` のメソッドを呼び出すとVSPackage 固有のオブジェクトを渡して応答します。  
  
4.  `IExtensibleObject` と `IVsExtensibleObject` の `QueryInterface` の呼び出しは失敗し環境は `IDispatch` の `QueryInterface` を呼び出します。  
  
## ドキュメント ウィンドウのオートメーション  
 標準の <xref:EnvDTE.Document> のオブジェクトはエディターは `IExtensibleObject` のインターフェイスを実装し`GetAutomationObject` に応答することにより `T:EnvDTE.Document` のオブジェクトの独自の実装を指定できますが環境でも使用できます。  
  
 また`IVsExtensibleObject` または `IExtensibleObject` インターフェイスの実装によって <xref:EnvDTE.Document.Object%2A> のメソッドによって取得される VSPackage 固有のオートメーション オブジェクトを提供できます。  [VSSDK のサンプル](../../misc/vssdk-samples.md) は RTF ドキュメント固有のオートメーション オブジェクトを提供します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
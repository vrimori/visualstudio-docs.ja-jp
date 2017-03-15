---
title: "オートメーション [オプション] ページのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツール オプション ページ [Visual Studio SDK] オートメーションによるサポート"
  - "オートメーション [Visual Studio SDK]、[ツール オプション ページを作成します。"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# オートメーション [オプション] ページのサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackages がユーザー設定を提供できる **オプション** \] ダイアログ ボックスを **ツール** メニュー \(\[ツール オプション ページ\) で [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] それらから利用できるように、オートメーション モデルとします。  
  
## ツール オプション ページ  
 作成する、 **ツール オプション** \] ページで、VSPackage で固有の VSPackage の実装の環境に返されるユーザー コントロールの実装を提供する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> メソッド \(またはマネージ コード、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> メソッド\)。  
  
 省略できますが、オートメーション モデルからこの新しいページへのアクセスを許可するように、強くお勧めします。 これは、次の手順を実行できます。  
  
1.  拡張、 <xref:EnvDTE._DTE.Properties%2A> IDispatch から派生したオブジェクトの実装を通じてオブジェクトです。  
  
2.  実装を返す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> メソッド \(またはマネージ コードに対して、 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> メソッド\) IDispatch から派生したオブジェクトにします。  
  
3.  オートメーション コンシューマーを呼び出すと、 <xref:EnvDTE._DTE.Properties%2A> カスタム メソッド **オプション** プロパティ ページで、環境を使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> メソッドは、ユーザー設定を取得する **ツール オプション** ページのオートメーションの実装です。  
  
4.  VSPackage のオートメーション オブジェクトを使用して、それぞれ提供 <xref:EnvDTE.Property> によって返される <xref:EnvDTE._DTE.Properties%2A>です。  
  
 カスタム ツール オプション ページを実装するサンプルについては、次を参照してください。 [VSSDK のサンプル](../../misc/vssdk-samples.md)します。  
  
## 参照  
 [プロジェクト オブジェクトを公開します。](../../extensibility/internals/exposing-project-objects.md)
---
title: "オートメーション [オプション] ページのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ffc56e4b36814a8bed7a0f93d66cc87c0b6fc466
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="automation-support-for-options-pages"></a>オートメーション [オプション] ページのサポート
Vspackage は、ユーザー設定を提供できます**オプション** ダイアログ ボックスを**ツール**メニュー ([ツール オプション] ページ) で[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ようにことができます、オートメーション モデルを使用できます。  
  
## <a name="tools-options-pages"></a>ツール オプション ページ  
 作成する、**ツール オプション** ページで、VSPackage の VSPackage の実装を通じて環境に返されるユーザー コントロールの実装を提供する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッド (またはマネージ コードに対して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッドの場合)。  
  
 省略可、ただし、オートメーション モデルからこの新しいページにアクセスできるように強くお勧めします。 これは、次の手順を行うことができます。  
  
1.  拡張、 <xref:EnvDTE._DTE.Properties%2A> IDispatch から派生したオブジェクトの実装を通してオブジェクト。  
  
2.  実装を返す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッド (またはマネージ コードに対して、<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>メソッド) IDispatch から派生したオブジェクトにします。  
  
3.  オートメーション コンシューマーを呼び出すと、<xref:EnvDTE._DTE.Properties%2A>カスタム メソッド**オプション**プロパティ ページで、環境を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッドは、ユーザー設定を取得する**ツール オプション**ページのオートメーション実装です。  
  
4.  各を提供する VSPackage のオートメーション オブジェクトを使用して<xref:EnvDTE.Property>によって返される<xref:EnvDTE._DTE.Properties%2A>です。  
  
 カスタム ツール オプション ページを実装するサンプルについては、次を参照してください。 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)です。  
  
## <a name="see-also"></a>参照  
 [プロジェクト オブジェクトの公開](../../extensibility/internals/exposing-project-objects.md)
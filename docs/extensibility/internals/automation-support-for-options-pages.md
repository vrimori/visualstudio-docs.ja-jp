---
title: オートメーション [オプション] ページのサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128573"
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
  
## <a name="see-also"></a>関連項目  
 [プロジェクト オブジェクトの公開](../../extensibility/internals/exposing-project-objects.md)
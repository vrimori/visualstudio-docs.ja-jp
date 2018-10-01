---
title: プロジェクト システムへの Web サービスの追加 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: 80de75b1b10a761e88b86c0982c0dc925c6eeeb4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537636"
---
# <a name="adding-web-services-to-project-systems"></a>プロジェクト システムへの Web サービスの追加
XML Web サービスは一般に、SOAP (Simple Object Access Protocol) プロトコルを使用して、プロジェクト システムにプログラム情報を返す URL を指定できるリソース。 使用して、VSPackage プロジェクト システムに Web サービスを統合することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>インターフェイス。  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>プロジェクト システムに Web サービスを追加するには  
  
1.  呼び出す`QueryService`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>インターフェイスを通じて<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg>サービス。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> メソッドを呼び出します。 渡す場合`pDiscoverySession`パラメーターとして`NULL`、探索セッションの作成、および以降を利用できるように、セッションがキャッシュされる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>インターフェイス。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> メソッドへのポインターを返します<xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> メソッドを呼び出します。 オートメーション オブジェクトと Web サービス参照フォルダーを渡す、`pUnkWebReferenceFolder`パラメーター。 Visual Studio 環境では、かどうか、Web サービスは既に存在し、確認します。 Web サービスが存在しない場合は、環境がダウンロードされ、フォルダーとフォルダーの子ノードに追加ファイル (.wsdl ファイルなど) に、Web サービスを追加します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>
---
title: "ソース コントロールの実行時の詳細情報 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9647f1f399b0d6516fe6475e6245c6834a0ea2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-runtime-details"></a>ソース コントロールの実行時の詳細
ユーザーは、ウィザードなどのオートメーション コント ローラーまたはソース管理にプロジェクトのファイルを追加したときに、プロジェクトはソース管理に追加します。 プロジェクトが指定されていません自体のソース管理されていることがあります。ソース管理をサポートしていますが、これを手動で追加する必要があります。  
  
## <a name="registering-with-a-source-control-package"></a>ソース管理パッケージを登録します。  
 プロジェクト内のファイルがソース管理に追加されると、環境を呼び出します<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>cookie としてソース管理システムで使用される 4 つの非透過的な文字列を提供します。 プロジェクト ファイルでこれらの文字列を格納します。 これらの文字列に渡されるソース コントロール スタブ (ソース管理パッケージを管理する Visual Studio コンポーネント) プロジェクトの種類の起動時に呼び出すことによって<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>です。 これは、さらに適切なソース管理パッケージを読み込んでの実装への呼び出しを転送`IVsSccManager2::RegisterSccProject`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)
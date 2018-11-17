---
title: ソース管理ランタイムの詳細 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3db90aaaccefb940c9cdea773b5b18f41f60d5d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756594"
---
# <a name="source-control-runtime-details"></a>ソース管理ランタイムの詳細
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクトは、ユーザーは、ウィザードなどのオートメーション コント ローラーまたはソース管理にプロジェクトのファイルを追加するとき、ソース管理に追加されます。 ソース管理されているある自体のプロジェクトが指定はしません。ソース管理をサポートしていますが、これを手動で追加する必要があります。  
  
## <a name="registering-with-a-source-control-package"></a>ソース管理のパッケージへの登録  
 ソース管理に、プロジェクト内のファイルが追加されると、環境を呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>cookie としてソース管理システムで使用される 4 つの不透明な文字列を提供します。 プロジェクト ファイル内には、これらの文字列を格納します。 これらの文字列渡す必要があります (ソース管理パッケージを管理する Visual Studio コンポーネント) のソース コントロール スタブをプロジェクトの種類の起動時に呼び出すことによって<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>します。 これでさらに適切なソース管理パッケージを読み込みますありの実装への呼び出しを転送`IVsSccManager2::RegisterSccProject`します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)


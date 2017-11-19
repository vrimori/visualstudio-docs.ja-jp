---
title: "テンプレートのポリシーと [プロパティ] ウィンドウ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72460f39cf63346106c2ccd81dc9ab16f8af78b9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="template-policy-and-the-properties-window"></a>テンプレートのポリシーと [プロパティ] ウィンドウ
エンタープライズ テンプレート プロジェクトをプロジェクトに含まれているときに、エンタープライズ テンプレート プロジェクトは、ポリシーを適用できます。 テンプレートのポリシーは、プロパティの既定値の設定、プロパティを非表示、プロパティを追加およびなどに使用できる制約システムになります。  
  
 内の情報の表示を制御するテンプレートのポリシーを使用して、**プロパティ**ウィンドウとは異なる実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>ソリューションまたはプロジェクト レベルでオブジェクトのプロパティを制限するテンプレートのポリシーを使用できますが、コンポーネント レベルでオブジェクトのプロパティを処理します。 要するにあの  
  
-   メソッドを実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>に表示される内容を決定する、**プロパティ**特定のオブジェクト ウィンドウ  
  
-   ソリューションおよびプロジェクト レベルに表示される内容を決定するテンプレートのポリシーを使用して、**プロパティ**以前に指定したオブジェクトのウィンドウ  
  
 特定のプロパティを選択的に制限するテンプレートのポリシーを使用して、**プロパティ**で指定した種類のプロジェクト項目のときにウィンドウが選択されている**ソリューション エクスプ ローラー**のすべてのメンバーに分けることができます開発チームは、プロジェクトで作業します。 など、テンプレートのポリシーを使用して、開発者がデータベースのすべての接続文字列情報を設定して、接続文字列を読み取り専用です。 この方法により、されるようにする各開発者に簡単な方法では、データ アクセスの正しいパスを提供できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)
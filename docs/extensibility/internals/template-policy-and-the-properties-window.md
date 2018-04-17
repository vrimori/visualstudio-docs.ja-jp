---
title: テンプレートのポリシーと [プロパティ] ウィンドウ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 759864533aa5bd3455a4e01c6642817107abb1a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="template-policy-and-the-properties-window"></a>テンプレートのポリシーと [プロパティ] ウィンドウ
エンタープライズ テンプレート プロジェクトをプロジェクトに含まれているときに、エンタープライズ テンプレート プロジェクトは、ポリシーを適用できます。 テンプレートのポリシーは、プロパティの既定値の設定、プロパティを非表示、プロパティを追加およびなどに使用できる制約システムになります。  
  
 内の情報の表示を制御するテンプレートのポリシーを使用して、**プロパティ**ウィンドウとは異なる実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ソリューションまたはプロジェクト レベルでオブジェクトのプロパティを制限するテンプレートのポリシーを使用できますが、コンポーネント レベルでオブジェクトのプロパティを処理します。 要するにあの  
  
-   メソッドを実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>に表示される内容を決定する、**プロパティ**特定のオブジェクト ウィンドウ  
  
-   ソリューションおよびプロジェクト レベルに表示される内容を決定するテンプレートのポリシーを使用して、**プロパティ**以前に指定したオブジェクトのウィンドウ  
  
 特定のプロパティを選択的に制限するテンプレートのポリシーを使用して、**プロパティ**で指定した種類のプロジェクト項目のときにウィンドウが選択されている**ソリューション エクスプ ローラー**のすべてのメンバーに分けることができます開発チームは、プロジェクトで作業します。 など、テンプレートのポリシーを使用して、開発者がデータベースのすべての接続文字列情報を設定して、接続文字列を読み取り専用です。 この方法により、されるようにする各開発者に簡単な方法では、データ アクセスの正しいパスを提供できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)
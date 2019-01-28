---
title: テンプレートのポリシーと、[プロパティ] ウィンドウ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b09d8dd21e65d1320aa6de78337ee8959fc42656
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001812"
---
# <a name="template-policy-and-the-properties-window"></a>テンプレート ポリシーとプロパティ ウィンドウ
エンタープライズ テンプレート プロジェクトをプロジェクトに含まれているときに、そのエンタープライズ テンプレート プロジェクトは、ポリシーを適用できます。 テンプレートのポリシーは、プロパティの既定値の設定、プロパティを非表示、プロパティを追加するために使用できる制約システムになります。  
  
 内の情報の表示を制御するテンプレートのポリシーを使用して、**プロパティ**ウィンドウとは異なる実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ソリューションまたはプロジェクト レベルでオブジェクトのプロパティを制限するテンプレートのポリシーを使用できますが、コンポーネント レベルでは、オブジェクトのプロパティを処理します。 要するにあの  
  
- メソッドを実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>に表示される内容を決定する、**プロパティ**特定のオブジェクト ウィンドウ  
  
- ソリューションおよびプロジェクト レベルに表示される内容を決定するテンプレートのポリシーを使用して、**プロパティ**以前に指定したオブジェクトのウィンドウ  
  
  特定のプロパティを選択的に制限するテンプレートのポリシーを使用して、**プロパティ**で指定した種類のプロジェクト項目のウィンドウが選択されている**ソリューション エクスプ ローラー**はのすべてのメンバーに利点があります開発チームは、プロジェクトで作業します。 たとえば、テンプレートのポリシーを使用して、開発者のデータベースのすべての接続文字列情報を設定でき読み取り専用接続文字列を作成できます。 この方法で、各開発者を確認するために簡単な方法は正しいパスを使用してデータにアクセスを提供できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)
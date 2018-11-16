---
title: プロパティ ウィンドウのオブジェクトのリスト |Microsoft Docs
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
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bbb9153a216b2d2fcc7cdeba0399aa60fc73881e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768906"
---
# <a name="properties-window-object-list"></a>プロパティ ウィンドウのオブジェクト一覧
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

オブジェクトの一覧で、**プロパティ**ウィンドウは、ドロップダウン リストを 1 つまたは複数選択したウィンドウ内で使用できる他のオブジェクトの選択を変更することができます。 呼び出しをトリガー内でのこの一覧から別のオブジェクトを選択する<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>に新しいオブジェクトが選択されている環境を通知します。 表示される情報、**プロパティ**ウィンドウは、新しく選択されたオブジェクトに関連付けられたプロパティを表示する変更します。  
  
## <a name="the-object-list"></a>オブジェクトの一覧  
 オブジェクトの一覧は、2 つのフィールドで構成されています: (太字で表示されます) オブジェクトの名前とオブジェクトの種類。  
  
 太字でオブジェクトの種類の左側に表示されるオブジェクト名は、オブジェクト自体から取得を使用して、`Name`によって指定されるプロパティ、<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>インターフェイス。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>、、唯一の方法で<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>、返します<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>インターフェイスのコクラスの。 **プロパティ**ウィンドウを使用して<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>ドロップダウン リストで、オブジェクト名として表示されると、コクラスの名前を取得します。  
  
 オブジェクトがない場合、`Name`プロパティ、名前は、オブジェクトの一覧の名前の領域には表示されません。 オブジェクトの一覧に表示名を使用する場合は、オブジェクトに Name プロパティを追加できます。  
  
 COM オブジェクトが実装していない場合<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>、**プロパティ**ウィンドウには、リストの左側にあるオブジェクト名の代わりにインターフェイス名が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)


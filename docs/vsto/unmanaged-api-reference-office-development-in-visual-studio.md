---
title: "アンマネージ API リファレンス (Visual Studio での Office 開発) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
ms.assetid: cdbc70b1-1f98-43dc-a619-07d805e53dce
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3a48af1199b041ef59c3e31e4e9496d78d21aec1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>アンマネージ API リファレンス (Visual Studio での Office 開発)
  2007 Microsoft Office system 以降では、Office アプリケーションを使用して、 [IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)に VSTO アドイン ローダー コンポーネントに含まれている呼び出しへのインターフェイス、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。 このコンポーネントは、VSTO マネージ アドインの読み込みに使用されます。このインターフェイスを実装することで、独自の VSTO アドイン ローダー コンポーネントを作成できます。  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)  
 Office アプリケーションでマネージ VSTO アドインの読み込みやアンロードを行うために実装できる COM インターフェイスです。  
  
  
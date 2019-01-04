---
title: アンマネージ API リファレンス (Visual Studio での Office 開発)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1ac4dfa9dd697993cffb527be521bd04c4c087ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991163"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>アンマネージ API リファレンス (Visual Studio での Office 開発)
  以降、2007 Microsoft Office system では、Office アプリケーションを使用して、 [IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)インターフェイスに含まれている VSTO アドイン ローダー コンポーネントへの呼び出しを[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。 このコンポーネントは、VSTO アドインの読み込みが管理のために使用されます。このインターフェイスを実装することで、独自の VSTO アドイン ローダー コンポーネントを作成できます。  
  
> [!NOTE]  
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、HTML5、JavaScript、CSS3、XML などのほぼすべての web プログラミング テクノロジを使用して、ビルドすることができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)  
 Office アプリケーションでマネージド VSTO アドインの読み込みやアンロードを行うために実装できる COM インターフェイスです。  

---
title: '方法: UML モデルの変更に対応 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: kamrani
ms.openlocfilehash: 3dfb863828c20df36b59a66d7198613b1a21eb29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725208"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>方法: UML モデル内で変更に応答する
Visual Studio の UML モデルで変更が生じたときに実行されるコードを作成できます。 このコードは、ユーザーが直接行った変更にも、他の Visual Studio 拡張機能による変更にも同様に応答します。 UML モデルをサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
> [!WARNING]
>  これらの手法は、UML API ではサポートされていません。 将来のバージョンの Visual Studio では機能しなくなる可能性があります。  
  
 サンプル コードについては、「 [UML: イベントと規則を使用して UML モデルの変更に応答](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)  
  
## <a name="see-also"></a>関連項目  
 [UML モデル内を移動します。](../modeling/navigate-the-uml-model.md)   
 [イベント ハンドラーには、モデルの外部で変更が反映されるまでください。](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [サンプル: Color by Stereotype](http://go.microsoft.com/fwlink/?LinkId=213841)
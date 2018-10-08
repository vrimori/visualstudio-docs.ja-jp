---
title: '方法: UML モデルの変更に対応 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: alancameronwills
ms.author: awills
manager: kamrani
ms.openlocfilehash: 07af0a9ee8fb31839343e853ee7175b204b7fe09
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534384"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>方法: UML モデル内で変更に応答する
Visual Studio の UML モデルで変更が生じたときに実行されるコードを作成できます。 このコードは、ユーザーが直接行った変更にも、他の Visual Studio 拡張機能による変更にも同様に応答します。 UML モデルをサポートする Visual Studio のバージョンを確認するを参照してください。[アーキテクチャとモデリング ツールのバージョンのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。  
  
> [!WARNING]
>  これらの手法は、UML API ではサポートされていません。 将来のバージョンの Visual Studio では機能しなくなる可能性があります。  
  
 サンプル コードについては、「 [UML: イベントと規則を使用して UML モデルの変更に応答](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)  
  
## <a name="see-also"></a>関連項目  
 [UML モデル内を移動します。](../modeling/navigate-the-uml-model.md)   
 [イベント ハンドラーには、モデルの外部で変更が反映されるまでください。](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [サンプル: Color by Stereotype](http://go.microsoft.com/fwlink/?LinkId=213841)
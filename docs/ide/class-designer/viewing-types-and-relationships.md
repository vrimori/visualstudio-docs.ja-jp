---
title: "型およびリレーションシップの表示 (クラス デザイナー) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- class diagrams
- types [Visual Studio], visualizing
- relationships, class diagrams
- types [Visual Studio], class diagrams
- relationships, visualizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e9ca80f3a3feb9655d53c6ee292f84c7c567d166
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="viewing-types-and-relationships-class-designer"></a>型およびリレーションシップの表示 (クラス デザイナー)

クラス デザイナーはクラス ダイアグラムを使用して、構成メンバー、共有している関係などの型の詳細情報を表示します。 実際のところ、これらのエンティティの視覚化はコードの動的ビューです。 つまり、デザイナーで型を編集し、エンティティのソース コードで、反映された編集内容を確認できます。 同様に、クラス ダイアグラムの同期が維持され、コード内のエンティティに加えられた変更が反映されます。

> [!NOTE]
> プロジェクトにクラス ダイアグラムが含まれ、プロジェクトが別のプロジェクト内の型を参照している場合、その型のプロジェクトをビルドするまで、クラス ダイアグラムに参照された型は表示されません。 同様に、外部エンティティのコードに加えられた場合、そのエンティティのプロジェクトをリビルドするまで、変更内容はダイアグラムに表示されません。

## <a name="see-also"></a>関連項目

[クラスおよび型のデザイン](designing-classes-and-types.md)  
[クラスおよび型のリファクタリング](refactoring-classes-and-types.md)  
[方法: クラス ダイアグラムをカスタマイズする](how-to-customize-class-diagrams.md)  
[クラス ダイアグラムの使用](working-with-class-diagrams.md)
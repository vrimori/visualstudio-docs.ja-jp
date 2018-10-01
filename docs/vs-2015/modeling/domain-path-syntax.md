---
title: ドメイン パス構文 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6df1f73614a8df59ee0bff8fb76610382d58b4e4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537808"
---
# <a name="domain-path-syntax"></a>ドメイン パス構文
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ドメイン パス構文](https://docs.microsoft.com/visualstudio/modeling/domain-path-syntax)します。  
  
DSL 定義は XPath に似た構文を使用して、モデル内の特定の要素を見つけます。  
  
 通常、この構文を直接扱う必要はありません。 DSL 詳細またはプロパティ ウィンドウで、下向き矢印をクリックし、パス エディターを使用できます。 ただし、パスがこの形式でフィールドに表示されるのは、エディターを使用した後です。  
  
 ドメイン パスは次のような形式になります。  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![CommentReferencesSubjects 参照リレーションシップ](../modeling/media/dsl-reference.png "dsl_reference")  
  
 構文はモデルのツリーを走査します。 たとえば、ドメイン リレーションシップ**CommentReferencesSubjects**上の図では、**サブジェクト**ロール。 パス セグメント **/!Subjectt**によりアクセスされる要素のパスが完了したことを指定します、**サブジェクト**ロール。  
  
 各セグメントの先頭はドメイン リレーションシップの名前になっています。 トラバーサルが要素からリレーションシップには、として、パス セグメントが表示されます*Relationship.PropertyName*します。 ホップがリンクから要素が、として、パス セグメントが表示されます*リレーションシップ/!RoleName*します。  
  
 スラッシュはパスの構文を区切ります。 各パス セグメントは要素からリンク (リレーションシップのインスタンス) へのホップか、リンクから要素へのホップのどちらかです。 パス セグメントは多くの場合、ペアで表示されます。 1 つのパス セグメントは要素からリンクへのホップを表し、次のセグメントはリンクから他端の要素へのホップを表します。 (どのリンクもリレーションシップ自体のソースまたはターゲットになりえます)。  
  
 要素からリンクへのホップに対して使用する名前はロールの `Property Name` の値です。 リンクから要素へのホップに対して使用する名前はターゲットのロール名です。  
  
## <a name="see-also"></a>関連項目  
 [モデル、クラス、およびリレーションシップについて](../modeling/understanding-models-classes-and-relationships.md)




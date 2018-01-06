---
title: "ドメイン パス構文 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: "25"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3a8694c3c2a0601d3ce616b593e4c652d959f59e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="domain-path-syntax"></a>ドメイン パス構文
DSL 定義は XPath に似た構文を使用して、モデル内の特定の要素を見つけます。  
  
 通常、この構文を直接扱う必要はありません。 DSL 詳細またはプロパティ ウィンドウで、下向き矢印をクリックし、パス エディターを使用できます。 ただし、パスがこの形式でフィールドに表示されるのは、エディターを使用した後です。  
  
 ドメイン パスは次のような形式になります。  
  
 *RelationshipName.PropertyName/!ロール*  
  
 ![CommentReferencesSubjects 参照リレーションシップ](../modeling/media/dsl_reference.png "dsl_reference")  
  
 構文はモデルのツリーを走査します。 たとえば、ドメイン リレーションシップ**CommentReferencesSubjects**上の図では、**サブジェクト**ロール。 パス セグメント**/!Subjectt**を介してアクセスされる要素のパスが終了するを指定します、**サブジェクト**ロール。  
  
 各セグメントの先頭はドメイン リレーションシップの名前になっています。 パスのセグメントとして表示されますが場合は、走査の各要素からリレーションシップを*Relationship.PropertyName*です。 ホップは、要素へのリンクからは、パスのセグメントとして表示されます*リレーションシップ/!RoleName*です。  
  
 スラッシュはパスの構文を区切ります。 各パス セグメントは要素からリンク (リレーションシップのインスタンス) へのホップか、リンクから要素へのホップのどちらかです。 パス セグメントは多くの場合、ペアで表示されます。 1 つのパス セグメントは要素からリンクへのホップを表し、次のセグメントはリンクから他端の要素へのホップを表します。 (どのリンクもリレーションシップ自体のソースまたはターゲットになりえます)。  
  
 要素からリンクへのホップに対して使用する名前はロールの `Property Name` の値です。 リンクから要素へのホップに対して使用する名前はターゲットのロール名です。  
  
## <a name="see-also"></a>参照  
 [モデル、クラス、およびリレーションシップについて](../modeling/understanding-models-classes-and-relationships.md)
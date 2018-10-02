---
title: 暗号化警告 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 947721de606cb6117ed2fd5f84bbc51e20e08203
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548325"
---
# <a name="cryptography-warnings"></a>暗号化警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[暗号化警告](https://docs.microsoft.com/visualstudio/code-quality/cryptography-warnings)します。  
  
暗号化警告では、暗号化を適切に使用することで、ライブラリとアプリケーションの安全性を高めています。 この警告によって、プログラムにセキュリティ上の欠陥が含まれるのを防ぐことができます。 この警告のいずれかを無効にする場合、明確にコードに理由を記載し、開発プロジェクトの指定されたセキュリティ管理者にも報告します。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA5350: 脆弱な暗号アルゴリズムを使用しないでください。](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|現在、さまざまな理由で弱い暗号化アルゴリズムとハッシュ関数が使用されていますが、保護対象のデータの機密性や整合性を保証するためにこれらを使用しないでください。        このルールは、コードで TripleDES、SHA1、または RIPEMD160 アルゴリズムが検出されるとトリガーされます。|  
|[CA5351 破られた暗号アルゴリズムを使用しないでください](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|破られた暗号アルゴリズムはセキュアであるとは見なされず、それらを使用しないことを強くお勧めします。 このルールは、コードに MD5 ハッシュ アルゴリズムや、DES か RC2 のいずれかの暗号化アルゴリズムが検出されるとトリガーされます。|




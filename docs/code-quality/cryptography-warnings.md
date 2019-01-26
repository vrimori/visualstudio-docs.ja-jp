---
title: 暗号化警告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15c70941f1c450b4df0e485266611835208306fd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928153"
---
# <a name="cryptography-warnings"></a>暗号化警告
暗号化警告では、暗号化を適切に使用することで、ライブラリとアプリケーションの安全性を高めています。 この警告によって、プログラムにセキュリティ上の欠陥が含まれるのを防ぐことができます。 この警告のいずれかを無効にする場合、明確にコードに理由を記載し、開発プロジェクトの指定されたセキュリティ管理者にも報告します。

|ルール|説明|
|----------|-----------------|
|[CA5350:脆弱な暗号アルゴリズムを使用しないでください。](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|現在、さまざまな理由で弱い暗号化アルゴリズムとハッシュ関数が使用されていますが、保護対象のデータの機密性や整合性を保証するためにこれらを使用しないでください。        このルールは、コードで TripleDES、SHA1、または RIPEMD160 アルゴリズムが検出されるとトリガーされます。|
|[CA5351 破られた暗号アルゴリズムを使用しないでください](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|破られた暗号アルゴリズムはセキュアであるとは見なされず、それらを使用しないことを強くお勧めします。 このルールは、コードに MD5 ハッシュ アルゴリズムや、DES か RC2 のいずれかの暗号化アルゴリズムが検出されるとトリガーされます。|
---
title: エディット コンティニュのエラーと警告 (c#) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: susanno
manager: douge
ms.openlocfilehash: 277208c47a51b1320a29d7cac869b0e786b7b291
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175956"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>エディット コンティニュのエラーと警告 (C#)
Visual C# エディット コンティニュで許可されていないコードのセクションを編集しました。  
  
 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] エディット コンティニュでは、プログラムの実行を中断モードで停止し、実行中のコードに変更を加えた後、変更結果を反映してプログラムを再開できます。  
  
 通常、クラスのパブリック構造体に影響を及ぼす宣言コードの編集は禁止されています。また、クラス内のメソッド、プロパティ本体、プライベート宣言に対する一部の編集も禁止されています。 可能な場合、エディット コンティニュで編集できないコードは明るい灰色で示され、エラー メッセージが表示されます。  
  
 エディット コンティニュでサポートされている編集の詳細については[!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]を参照してください[サポートされているコード変更 (c#)](../debugger/supported-code-changes-csharp.md)します。 特定のエラーや警告に関する詳細情報が必要な場合は、MSDN の [Visual C# IDE フォーラム](http://go.microsoft.com/fwlink/?LinkId=214693)で質問を投稿したり、回答を検索したりできます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  **[デバッグ]** メニューの **[元に戻す]** をクリックし、変更を元に戻します。  
  
     - または -  
  
2.  デバッグ セッションを停止し、編集を加えた後で新しいデバッグ セッションを開始します。  
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュ (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
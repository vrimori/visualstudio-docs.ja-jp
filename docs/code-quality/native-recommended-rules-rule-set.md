---
title: "&quot;ネイティブ推奨規則&quot; 規則セット | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d845b5a-1b75-4e9d-861a-7c59cb7752af
caps.latest.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 3
---
# &quot;ネイティブ推奨規則&quot; 規則セット
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ネイティブは最も重要内の規則に重点を置く推奨し、セキュリティ ホール、アプリケーションを含むネイティブ コードの一般的な問題は、クラッシュします。ネイティブ プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。この規則セットは、Visual Studio Professional Edition 以上で動作するように設計されています。  
  
|規則|説明|  
|--------|--------|  
|[C6001](../code-quality/c6001.md)|初期化されていないメモリの使用|  
|[C6011](../code-quality/c6011.md)|Null ポインターの逆参照|  
|[C6029](../code-quality/c6029.md)|未確認の値の使用|  
|[C6031](../code-quality/c6031.md)|戻り値の無視|  
|[C6053](../code-quality/c6053.md)|呼び出しの 0 での終了|  
|[C6054](../code-quality/c6054.md)|0 での終了がない|  
|[C6059](../code-quality/c6059.md)|不適切な連結|  
|[C6063](../code-quality/c6063.md)|Format 関数への文字列引数がない|  
|[C6064](../code-quality/c6064.md)|Format 関数への整数引数がない|  
|[C6066](../code-quality/c6066.md)|Format 関数へのポインター引数がない|  
|[C6067](../code-quality/c6067.md)|Format 関数への文字列ポインター引数がない|  
|[C6101](../code-quality/c6101.md)|初期化されていないメモリを返します|  
|[C6200](../code-quality/c6200.md)|インデックスがバッファーの最大値を超過|  
|[C6201](../code-quality/c6201.md)|インデックスがスタック バッファーの最大値を超過|  
|[C6214](../code-quality/c6214.md)|HRESULT から BOOL への無効なキャスト|  
|[C6215](../code-quality/c6215.md)|BOOL から HRESULT への無効なキャスト|  
|[C6216](../code-quality/c6216.md)|BOOL から HRESULT へのコンパイラ挿入された無効なキャスト|  
|[C6217](../code-quality/c6217.md)|NOT での無効な HRESULT テスト|  
|[C6220](../code-quality/c6220.md)|無効な HRESULT は \-1 と比較します。|  
|[C6226](../code-quality/c6226.md)|\-1 への無効な HRESULT の割り当て|  
|[C6230](../code-quality/c6230.md)|ブール値としての無効な HRESULT 使用|  
|[C6235](../code-quality/c6235.md)|以外の定数と論理 OR|  
|[C6236](../code-quality/c6236.md)|論理 OR 以外の定数と|  
|[C6237](../code-quality/c6237.md)|ゼロと論理 AND 副作用が失われます。|  
|[C6242](../code-quality/c6242.md)|ローカル アンワインドの強制|  
|[C6248](../code-quality/c6248.md)|Null DACL の作成|  
|[C6250](../code-quality/c6250.md)|解放されていないアドレス記述子|  
|[C6255](../code-quality/c6255.md)|Alloca の保護されていない使用|  
|[C6258](../code-quality/c6258.md)|を使用してスレッドを終了します。|  
|[C6259](../code-quality/c6259.md)|実行されないコード ビットごとの OR 限られたスイッチ|  
|[C6260](../code-quality/c6260.md)|バイト算術の使用|  
|[C6262](../code-quality/c6262.md)|過剰なスタック使用|  
|[C6263](../code-quality/c6263.md)|ループでの Alloca の使用|  
|[C6268](../code-quality/c6268.md)|キャストでのかっこの不足|  
|[C6269](../code-quality/c6269.md)|ポインターの逆参照の無視|  
|[C6270](../code-quality/c6270.md)|Format 関数への Float 引数がない|  
|[C6271](../code-quality/c6271.md)|Format 関数への余分な引数|  
|[C6272](../code-quality/c6272.md)|Format 関数への Float でない引数|  
|[C6273](../code-quality/c6273.md)|関数の書式を指定する整数以外 Argumen|  
|[C6274](../code-quality/c6274.md)|Format 関数への文字でない引数|  
|[C6276](../code-quality/c6276.md)|無効な文字列のキャスト|  
|[C6277](../code-quality/c6277.md)|無効な CreateProcess 呼び出し|  
|[C6278](../code-quality/c6278.md)|配列の New とスカラーの Delete の不一致|  
|[C6279](../code-quality/c6279.md)|スカラーの New と配列の Delete の不一致|  
|[C6280](../code-quality/c6280.md)|メモリの割り当てと解放の不一致|  
|[C6281](../code-quality/c6281.md)|ビットごとと関係の優先順位|  
|[C6282](../code-quality/c6282.md)|代入をテストに置き換え|  
|[C6283](../code-quality/c6283.md)|プリミティブな配列の New とスカラーの Delete の不一致|  
|[C6284](../code-quality/c6284.md)|Format 関数への無効なオブジェクト引数|  
|[C6285](../code-quality/c6285.md)|論理 OR の定数|  
|[C6286](../code-quality/c6286.md)|ゼロ以外の論理 OR や副作用|  
|[C6287](../code-quality/c6287.md)|冗長テスト|  
|[C6288](../code-quality/c6288.md)|相互包含は論理的および false|  
|[C6289](../code-quality/c6289.md)|相互排他が論理 OR 当てはまります。|  
|[C6290](../code-quality/c6290.md)|論理否定演算子ビットごとの and 優先順位|  
|[C6291](../code-quality/c6291.md)|論理否定演算子ビットごとの OR の優先順位|  
|[C6292](../code-quality/c6292.md)|ループ カウントの最大値超過|  
|[C6293](../code-quality/c6293.md)|ループ カウントの最小値未満|  
|[C6294](../code-quality/c6294.md)|ループ本体が実行されない|  
|[C6295](../code-quality/c6295.md)|無限ループ|  
|[C6296](../code-quality/c6296.md)|ループが 1 度だけ実行される|  
|[C6297](../code-quality/c6297.md)|シフトの結果がより大きいサイズにキャストされる|  
|[C6299](../code-quality/c6299.md)|ビット フィールドとブール値の比較|  
|[C6302](../code-quality/c6302.md)|Format 関数への無効な文字列引数|  
|[C6303](../code-quality/c6303.md)|Format 関数への無効なワイド文字列引数|  
|[C6305](../code-quality/c6305.md)|サイズと数の使用の不一致|  
|[C6306](../code-quality/c6306.md)|不適切な変数引数の関数呼び出し|  
|[C6308](../code-quality/c6308.md)|Realloc のリーク|  
|[C6310](../code-quality/c6310.md)|無効な例外フィルター定数|  
|[C6312](../code-quality/c6312.md)|Exception Continue Execution ループ|  
|[C6314](../code-quality/c6314.md)|ビットごとの OR の優先順位|  
|[C6317](../code-quality/c6317.md)|存在しない補完|  
|[C6318](../code-quality/c6318.md)|Exception Continue Search|  
|[C6319](../code-quality/c6319.md)|コンマによる無視|  
|[C6324](../code-quality/c6324.md)|文字列比較でない文字列コピー|  
|[C6328](../code-quality/c6328.md)|引数の型の不一致の可能性|  
|[C6331](../code-quality/c6331.md)|VirtualFree の無効なフラグ|  
|[C6332](../code-quality/c6332.md)|VirtualFree の無効なパラメーター|  
|[C6333](../code-quality/c6333.md)|VirtualFree の無効なサイズ|  
|[C6335](../code-quality/c6335.md)|プロセス ハンドルのリーク|  
|[C6381](../code-quality/c6381.md)|シャットダウン情報がない|  
|[C6383](../code-quality/c6383.md)|要素数とバイト数のバッファー オーバーラン|  
|[C6384](../code-quality/c6384.md)|ポインターのサイズの除算|  
|[C6385](../code-quality/c6385.md)|読み取りのオーバーラン|  
|[C6386](../code-quality/c6386.md)|書き込みのオーバーラン|  
|[C6387](../code-quality/c6387.md)|無効なパラメーター値|  
|[C6388](../code-quality/c6388.md)|無効なパラメーター値|  
|[C6500](../code-quality/c6500.md)|無効な属性プロパティ|  
|[C6501](../code-quality/c6501.md)|属性プロパティ値の競合|  
|[C6503](../code-quality/c6503.md)|参照は Null にはできない|  
|[C6504](../code-quality/c6504.md)|非ポインターでの Null|  
|[C6505](../code-quality/c6505.md)|Void での MustCheck|  
|[C6506](../code-quality/c6506.md)|非ポインターまたは配列でのバッファー サイズ|  
|[C6507](http://msdn.microsoft.com/ja-jp/18f88cd1-d035-4403-a6a4-12dd0affcf21)|逆参照ゼロの空白の不一致|  
|[C6508](../code-quality/c6508.md)|定数での書き込みアクセス|  
|[C6509](../code-quality/c6509.md)|前提条件で使用される Return|  
|[C6510](../code-quality/c6510.md)|非ポインターでの Null 終了|  
|[C6511](../code-quality/c6511.md)|MustCheck は Yes または No でなければならない|  
|[C6513](../code-quality/c6513.md)|バッファー サイズのない要素サイズ|  
|[C6514](../code-quality/c6514.md)|バッファー サイズが配列サイズを超過|  
|[C6515](../code-quality/c6515.md)|非ポインターでのバッファー サイズ|  
|[C6516](../code-quality/c6516.md)|属性にプロパティがない|  
|[C6517](../code-quality/c6517.md)|読み取り可能でないバッファーでの有効なサイズ|  
|[C6518](../code-quality/c6518.md)|書き込み可能でないバッファーでの書き込み可能サイズ|  
|[C6519](http://msdn.microsoft.com/ja-jp/2b6326b0-0539-4d26-8fb1-720114933232)|無効な注釈です: 「NeedsRelease」プロパティの値がはいといいえの指定|  
|[C6521](http://msdn.microsoft.com/ja-jp/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|無効なサイズの文字列参照解除|  
|[C6522](../code-quality/c6522.md)|無効なサイズの文字列型|  
|[C6523](http://msdn.microsoft.com/ja-jp/11397a31-b224-46b0-afb7-d49ca576a3bb)|無効なサイズを文字列パラメーター|  
|[C6525](../code-quality/c6525.md)|無効なサイズの到達不能な場所の文字列|  
|[C6526](http://msdn.microsoft.com/ja-jp/59c590c7-0098-4166-a1ac-87f324596002)|無効なサイズの文字列バッファーの型|  
|[C6527](../code-quality/c6527.md)|無効な注釈です: 'NeedsRelease' プロパティは、void 型の値では使用できません|  
|[C6530](../code-quality/c6530.md)|認識されない書式指定文字列スタイル|  
|[C6540](../code-quality/c6540.md)|この関数の属性の注釈を使用すると、既存の\_\_declspec 注釈がすべて無効になります。|  
|[C6551](../code-quality/c6551.md)|無効なサイズ指定です: 解析できる式|  
|[C6552](../code-quality/c6552.md)|無効な Deref\= または Notref\=: 解析できる式|  
|[C6701](../code-quality/c6701.md)|値が有効な Yes\/No\/Maybe 値ではありません。|  
|[C6702](../code-quality/c6702.md)|値は、文字列値ではありません。|  
|[C6703](../code-quality/c6703.md)|value が数ではありません。|  
|[C6704](../code-quality/c6704.md)|予期しない注釈の式のエラー|  
|[C6705](../code-quality/c6705.md)|注釈の引数の予期された数は、注釈の引数の実際の数は一致しません|  
|[C6706](../code-quality/c6706.md)|注釈の予期しないエラーの注釈|  
|[C6995](../code-quality/c6995.md)|XML ログ ファイルを保存できませんでした|  
|[C26100](../code-quality/c26100.md)|競合状態|  
|[C26101](../code-quality/c26101.md)|適切なインタロック操作の使用の失敗|  
|[C26110](../code-quality/c26110.md)|呼び出し元でのロックの保持の失敗|  
|[C26111](../code-quality/c26111.md)|呼び出し元でのロックの解放の失敗|  
|[C26112](../code-quality/c26112.md)|呼び出し元がロックを保持できない|  
|[C26115](../code-quality/c26115.md)|ロックの解放の失敗|  
|[C26116](../code-quality/c26116.md)|ロックの取得または保持の失敗|  
|[C26117](../code-quality/c26117.md)|保持されていないロックの解放|  
|[C26140](../code-quality/c26140.md)|同時実行 SAL 注釈のエラーです。|  
|[C28020](../code-quality/c28020.md)|式はこの呼び出しで true ではありません|  
|[C28021](../code-quality/c28021.md)|注釈が付けられているパラメーターはポインターである必要があります|  
|[C28022](../code-quality/c28022.md)|この関数のクラスを定義するために使用される関数の typedef クラスと一致しません。|  
|[C28023](../code-quality/c28023.md)|割り当てられた場合や、渡された関数はクラスの 1 個以上の\_Function\_class\_の注釈が必要です。|  
|[C28024](../code-quality/c28024.md)|に割り当てられた関数ポインターは、関数のクラス リストに含まれていない関数クラスが指定されます。|  
|[C28039](../code-quality/c28039.md)|実パラメーターの型は、型と完全に一致する必要があります|  
|[C28112](../code-quality/c28112.md)|インタロックされた関数でアクセスされる変数は、インタロック関数によって常にアクセスする必要があります。|  
|[C28113](../code-quality/c28113.md)|Interlocked 関数経由でローカル変数にアクセスしています|  
|[C28125](../code-quality/c28125.md)|関数は try\/except ブロック内から呼び出される必要があります|  
|[C28137](../code-quality/c28137.md)|可変個の引数が a \(リテラル定数\) 必要があります。|  
|[C28138](../code-quality/c28138.md)|定数の引数は、変数である必要があります|  
|[C28159](../code-quality/c28159.md)|代わりに、別の関数を使用して検討。|  
|[C28160](../code-quality/c28160.md)|Error 注釈|  
|[C28163](../code-quality/c28163.md)|関数は try\/except ブロック内から呼び出さないでください|  
|[C28164](../code-quality/c28164.md)|引数はオブジェクト \(ポインターへのポインターではなく\) へのポインターを受け取る関数に渡します。|  
|[C28182](../code-quality/c28182.md)|NULL ポインターを逆参照しています。  ポインターは別のポインターと同じ null 値が含まれます。|  
|[C28183](../code-quality/c28183.md)|引数は 1 つの値である可能性があり、ポインターで見つかった値のコピーです|  
|[C28193](../code-quality/c28193.md)|変数が確認される値を保持します。|  
|[C28196](../code-quality/c28196.md)|要件が満たされていません。\(式は true に評価されません\)|  
|[C28202](../code-quality/c28202.md)|静的でないメンバーへの参照が正しくありません|  
|[C28203](../code-quality/c28203.md)|クラス メンバーへのあいまいな参照です。|  
|[C28205](../code-quality/c28205.md)|\_Success\_ または \_On\_failure\_ が無効なコンテキスト内で使用されています|  
|[C28206](../code-quality/c28206.md)|左のオペランドは構造体、使用"ポイント\>|  
|[C28207](../code-quality/c28207.md)|左のオペランドは構造体、使用「」。|  
|[C28209](../code-quality/c28209.md)|シンボルの宣言に競合する宣言が含まれています|  
|[C28210](../code-quality/c28210.md)|\_\_on\_failure のコンテキストの注釈はコンテキストに明示前にある必要があります。|  
|[C28211](../code-quality/c28211.md)|SAL\_context には静的コンテキスト名が必要です|  
|[C28212](../code-quality/c28212.md)|注釈にはポインター式が必要です|  
|[C28213](../code-quality/c28213.md)|\_Use\_decl\_annotations\_ 注釈は、変更、先行する宣言なしで、参照に使用される必要があります。|  
|[C28214](../code-quality/c28214.md)|属性パラメーター名は、p1...p9 である必要があります|  
|[C28215](../code-quality/c28215.md)|typefix は、既に typefix のあるパラメーターには適用できません|  
|[C28216](../code-quality/c28216.md)|checkReturn の注釈は、関数のパラメーターの事後条件にのみ適用されます。|  
|[C28217](../code-quality/c28217.md)|関数では、注釈に渡すパラメーターの個数はファイルにある一致しません。|  
|[C28218](../code-quality/c28218.md)|関数の paramteer では、注釈のパラメーターはファイルにある一致しません。|  
|[C28219](../code-quality/c28219.md)|注釈 \(注釈のパラメーター\) には列挙型のメンバーが必要です|  
|[C28220](../code-quality/c28220.md)|整数式は、注釈で注釈のパラメーターが必要です。|  
|[C28221](../code-quality/c28221.md)|注釈のパラメーターには文字列式が必要です|  
|[C28222](../code-quality/c28222.md)|注釈には \_\_yes、\_\_no、または \_\_maybe が必要です|  
|[C28223](../code-quality/c28223.md)|注釈、パラメーターの予期されるトークンまたは識別子が見つかりませんでした|  
|[C28224](../code-quality/c28224.md)|注釈にはパラメーターが必要です|  
|[C28225](../code-quality/c28225.md)|注釈の必須パラメーターの正しい数が見つかりませんでした|  
|[C28226](../code-quality/c28226.md)|注釈は、PrimOp \(現在の宣言内\) になることもできません|  
|[C28227](../code-quality/c28227.md)|注釈は、PrimOp \(前の宣言を参照\) になることもできません|  
|[C28228](../code-quality/c28228.md)|注釈パラメーター: 型の注釈は使用できません|  
|[C28229](../code-quality/c28229.md)|注釈はパラメーターをサポートしません|  
|[C28230](../code-quality/c28230.md)|パラメーターの型とメンバーはありません。|  
|[C28231](../code-quality/c28231.md)|注釈は配列でのみ有効です|  
|[C28232](../code-quality/c28232.md)|前に、注釈に適用されないポスト、または deref|  
|[C28233](../code-quality/c28233.md)|前に、POST、または deref はブロックに適用します。|  
|[C28234](../code-quality/c28234.md)|\_\_at の式は、現在の関数には適用されません。|  
|[C28235](../code-quality/c28235.md)|関数は、注釈としてスタンドアロンのできません|  
|[C28236](../code-quality/c28236.md)|注釈は式では使用できません|  
|[C28237](../code-quality/c28237.md)|パラメーターの注釈はサポートされていません。|  
|[C28238](../code-quality/c28238.md)|注釈は、パラメーターの値 stringValue と longValue 1 を超える場合があります。  paramn\=xxx を使用してください|  
|[C28239](../code-quality/c28239.md)|パラメーターの注釈の値、stringValue、または longValue;があります。と paramn\=xxx。  paramn\=xxx のみを使用してください|  
|[C28240](../code-quality/c28240.md)|パラメーターに注釈を付けることに param2 param1 はありません|  
|[C28241](../code-quality/c28241.md)|パラメーターを使用する関数の注釈が認識されない|  
|[C28243](../code-quality/c28243.md)|パラメーターを使用する関数の注釈を実際の型で注釈が付けられた割り当てよりも多くの逆参照が必要です。|  
|[C28244](../code-quality/c28244.md)|関数の注釈に unparseable パラメーターまたは外部注釈があります。|  
|[C28245](../code-quality/c28245.md)|関数の注釈は非メンバー関数の" this "注釈を|  
|[C28246](../code-quality/c28246.md)|関数のパラメーター注釈は、パラメーターの型と一致しません。|  
|[C28250](../code-quality/c28250.md)|関数の競合する注釈: 前のインスタンスにエラーがあります。|  
|[C28251](../code-quality/c28251.md)|関数の競合する注釈: このインスタンスにエラーがあります。|  
|[C28252](../code-quality/c28252.md)|関数の競合する注釈: パラメーターにこのインスタンスの別の注釈があります。|  
|[C28253](../code-quality/c28253.md)|関数の競合する注釈: パラメーターにこのインスタンスの別の注釈があります。|  
|[C28254](../code-quality/c28254.md)|dynamic\_cast が\<\>注釈 \(\) でサポートされていません|  
|[C28262](../code-quality/c28262.md)|注釈の構文エラーは、注釈の関数で、見つかりました|  
|[C28263](../code-quality/c28263.md)|条件で構文エラーは、基本的な注釈に見つかりました|  
|[C28264](http://msdn.microsoft.com/ja-jp/bf6ea983-a06e-4752-a042-747a7dbf338c)|結果リストの値は定数である必要があります。|  
|[C28267](../code-quality/c28267.md)|注釈の構文エラーは、関数で見つかった注釈です。|  
|[C28272](../code-quality/c28272.md)|確認が関数宣言と矛盾しているときに、関数パラメーターの注釈|  
|[C28273](../code-quality/c28273.md)|関数の場合、手掛かりが関数宣言と一致しません。|  
|[C28275](../code-quality/c28275.md)|\_Macro\_value\_ へのパラメーターが null です|  
|[C28279](../code-quality/c28279.md)|シンボルについては、「 \(\) 」が見つかりました。一致の末尾「なし"|  
|[C28280](../code-quality/c28280.md)|シンボルについては、「終了」が一致しない中「で始まり」|  
|[C28282](../code-quality/c28282.md)|書式指定文字列は、前提条件の中に存在する必要があります|  
|[C28285](../code-quality/c28285.md)|関数の場合、パラメーターの構文エラー|  
|[C28286](../code-quality/c28286.md)|関数の場合、最後の近くに構文エラーがあります。|  
|[C28287](../code-quality/c28287.md)|関数の場合、\_At\_\(\) の注釈 \(認識されないパラメーター名\) の構文エラー|  
|[C28288](../code-quality/c28288.md)|関数の場合、\_At\_\(\) の注釈 \(無効なパラメーターの名前\) の構文エラー|  
|[C28289](../code-quality/c28289.md)|関数の場合: ReadableTo または WritableTo にパラメーターとして制限仕様はありませんでした。|  
|[C28290](../code-quality/c28290.md)|関数の注釈は、パラメーターの実際の数よりも多くの外部が含まれます。|  
|[C28291](../code-quality/c28291.md)|deref レベル 0 の投稿の空白と notnull は関数ごとに無意味です。|  
|[C28300](../code-quality/c28300.md)|演算子に対する互換性のない型の、式のオペランドです|  
|[C28301](../code-quality/c28301.md)|関数の最初の宣言の注釈はありません。|  
|[C28302](../code-quality/c28302.md)|追加\_Deref\_の演算子は、注釈で見つかりました。|  
|[C28303](../code-quality/c28303.md)|あいまいな\_Deref\_の演算子は、注釈で見つかりました。|  
|[C28304](../code-quality/c28304.md)|不適切に配置\_Notref\_の演算子はトークンに適用見つかりました。|  
|[C28305](../code-quality/c28305.md)|トークンを解析することが検出されると、エラーが発生します。|  
|[C28306](../code-quality/c28306.md)|パラメーターの注釈はたれかかっています。|  
|[C28307](../code-quality/c28307.md)|パラメーターの注釈はたれかかっています。|  
|[C28350](../code-quality/c28350.md)|注釈は、条件付きで適用できない状況を示します。|  
|[C28351](../code-quality/c28351.md)|注釈は、動的な値 \(変数\) が条件のどこに使用できないことを示します。|
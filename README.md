clc();

raw_sim = [];
raw_dis = [];
mean_sim = [];
mean_dis = [];
sd_sim = [];
sd_dis = [];

name = importdata('C:\Users\sura\Desktop\Dataset\UCR 47 dataset\47_Trainingset_Name.txt');
[number_of_file nc] = size(name);
Y = []; %% use in plot error graph
E = []; %% use in plot error graph
kendall_tau = [];
for round=1:number_of_file
    
file = {'C:\Users\sura\Desktop\BCI_workspace\New_Similarity\'};
file = strcat(file,name{round});
file_dtw = strcat(file,'_TRAIN_DTW_dist_column_query_row_cand.txt');
file_dtw = char(file_dtw)

file_sim = strcat(file,'_TRAIN_DTW_dist_column_query_row_cand.txt');
file_sim = char(file_sim)

ans_dtw = importdata(file_dtw);
[row,column] = size(ans_dtw);
ans_similar = importdata(file_sim);

% [B_d,I_d] = sort(ans_dtw);
% [B_s,I_s] = sort(ans_similar,'descend');
% 
% raw_dis = [raw_dis, B_d(1:4,1)'];
% mean_dis = [mean_dis, mean(B_d(1:4,1))];
% sd_dis = [sd_dis, std(B_d(1:4,1))];
% raw_sim = [raw_sim, B_s(1:4,1)'];
% mean_sim = [mean_sim, mean(B_s(1:4,1))];
% sd_sim = [sd_sim, std(B_s(1:4,1))];






% %%%%%%%%%%%%%%%%% Kandell tau rank correlation ......    using I_d as reference
% rank_a = (1:row)';
% rank_b = [];
% for i=1:row
%     rank_b = [rank_b;find(I_s == I_d(i))];
% end
% rank_b;
% concordant = 0;
% discordant = 0;
% for i=1:row-1
%     concordant = concordant + size(find(rank_b(i:end)>rank_b(i)),1);
%     discordant = discordant + size(find(rank_b(i:end)<rank_b(i)),1);
% end
% kendall_tau = [kendall_tau, (concordant-discordant) / (concordant+discordant)];
% fprintf('kendall tau = %f\n\n',kendall_tau(round));

end

% fprintf('mean_dis = %f , sd = %f\n',mean(raw_dis),std(raw_dis));
% fprintf('mean_sim = %f , sd = %f\n',mean(raw_sim),std(raw_sim));

% figure();
% errorbar([1:47],mean_dis,sd_dis,'x');
% ylabel('mean +- sd of the dtw for the first 4 rank that most similar');
% xlabel('dataset');
% xlim([0 47]);
% saveas(gcf,'C:\Users\sura\Desktop\BCI_workspace\รูป Threshold testing\dtw mean_sd of the dtw for the first 4 rank that most similar','epsc');

% figure();
% errorbar([1:47],mean_sim,sd_sim,'x');
% ylabel('mean +- sd of the similarity for the first 4 rank that most similar');
% xlabel('dataset');
% xlim([0 47]);
% ylim([0 1.0]);
% saveas(gcf,'C:\Users\sura\Desktop\BCI_workspace\รูป Threshold testing\similarity mean_sd of the dtw for the first 4 rank that most similar','epsc');


% figure;
% plot(kendall_tau,'x');
% ylim([0.0 1.0]);
% ylabel('Kendall tau correlation');
% xlabel('dataset');
% xlim([0 47]);
% saveas(gcf,'C:\Users\Tong\Desktop\BCI_workspace\รูป Threshold testing\Kendall tau correlation','epsc');
% fprintf('mean kendall tau = %f , sd kendall_tau = %f\n\n',mean(kendall_tau),std(kendall_tau));

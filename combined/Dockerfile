FROM python:3

WORKDIR /usr/src/app

RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get install make -y
RUN apt-get install git -y
RUN git clone https://github.com/Openfisca-NSW/openfisca_nsw_base.git 
RUN git clone https://github.com/Openfisca-NSW/openfisca_nsw_API.git 
RUN git clone https://github.com/Openfisca-NSW/openfisca_nsw_community_gaming.git 
RUN git clone https://github.com/Openfisca-NSW/openfisca_nsw_rules_kids_vouchers.git 
# RUN git clone https://github.com/Openfisca-NSW/openfisca_nsw_ess_nabers.git 
RUN git clone https://github.com/angus151/openfisca_nsw_ess_nabers.git
RUN sed -i '46d' openfisca_nsw_API/Makefile
RUN make -C openfisca_nsw_API

RUN apt-get install npm -y
RUN git clone https://github.com/angus151/openfisca_nsw_form_generator.git 
RUN cd openfisca_nsw_form_generator/form-generator/ && npm i --no-fund --prod

EXPOSE 4000
EXPOSE 80:4200

CMD openfisca serve --workers=1 --country-package openfisca_nsw_base --extensions openfisca_nsw_ess_nabers openfisca_nsw_rules_kids_vouchers openfisca_nsw_community_gaming openfisca_nsw_API --bind 0.0.0.0:4000